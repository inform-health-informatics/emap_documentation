# EMAP's use of RabbitMQ 

 

RabbitMQ is a light weight open source message broker which allows multiple publishers 
i.e. senders of information and multiple subscribers i.e. receivers of information. 
It provides several configuration options that allow you to determine when the queue thinks it has finished with a piece of information and provide back up options suitable to individual requirements. 

 

This document is not an in depth look at RabbitMQ. It is a summary of the configuration and RabbitMQ features used within the EMAP pipeline. 

 

The EMAP pipeline currently has two publishers (the live hl7 processor and the hoover) and one subscriber, the EMAP core processor which writes to the star database. We use a very tight configuration to avoid any loss of data. 

 

## The 'at least once' strategy 

  

We deploy the RabbitMQ 'at least once' strategy. When a message is received by RabbitMQ from the publisher it is immediately persisted to disk. 
The ensures that in the event of a system crash the data can be recovered. Following a crash when the system reboots messages are retrieved from the disk and no data is lost. 
Once the message is written to disk RabbitMQ informs the publisher that it has successfully received the message. 
If the queue is full, the publisher will wait and retry to send the message until RabbitMQ acknowledges it has a copy. 
This means that the publisher does not consider itself finished with a message until it receives an acknowledgment from RabbitMQ that the message has been successfully received. 
If there is an issue between sending a message and receiving an acknowledgement, the publisher will resend the message until such time as it gets the acknowledgment.  

 

Once RabbitMQ has successfully acknowledged receipt of the message from the publisher it then sends the message to the subscriber when requested. 
The subscriber received the message and does any necessary processing, in this case writing to the star database and once this is done the subscriber sends an acknowledgment to RabbitMQ to say that it has successfully received and dealt with the message. 
Only when RabbitMQ receives this acknowledgement does it delete the message from its queue.  
Again, if the system fails between sending the message and receiving the acknowledgement, then the message can be recovered and resent.        
This is part of the rationale for using RabbitMQ. 
By waiting and holding onto messages until they are needed, it acts as a reliable message buffer that cleanly allows all the different services, which work at varying rates, to work smoothly together.
 

On occasion this process means that a message may be sent and received more than once and we have duplicate messages. 
Our processing of messages into the database is written to handle this situation and remove duplicates. 
This strategy does however ensure that we receive all messages. 
Considering the trade-off between needing to catch duplicates and losing messages resulted in the deliberate decision to configure RabbitMQ in this way to ensure all messages are received. 
This decision proved fortuitous as it transpires that we do receive duplicate messages as pat of our normal data flow and thus this processing step was needed. 

 

### Publishers 

 

HL7 messages from several live streams are fed into the IDS which stores the message plus unique id. The 'hl7processor' takes messages as they arrive in the IDS. Since the IDS is persistent, this allows us to restart the system from the point at which the IDS first received data and thus recover data from the live data stream going back in time.

The 'hoover' is used when we need to do a data extract direct from existing databases. This may be to capture information that existed before a particular stream went live, to extract metadata or to access data from the nightly dump to Caboodle that allows EMAP to store data that cannot yet be accessed as a live stream. 

Each pubisher writes to a queue which is published to the core processor and sent to RabbitMQ in order: hl7processor then hoover. Using the Java Spring framework and in particular, '''spring-amqp'''  gives priority to them in the order specified. This means the hl7processor will always take priority over the hoover publisher; any message being received from this publisher will be dealt with immediately whilst putting any messages from the hoover on hold. Note it is hard to find documentation that confirms this but our own testing shows Spring seems to follow this approach. 

 

## Application 

 

EMAP is run as a collection of docker containers, each providing a single service such as RabbitMQ. We take the latest RabbitMQ management image from dockerhub and configure it as required. This involves setting ports, authentication and details such as maximum queue size and waiting times. As the RabbitMQ component sits in the middle of the pipeline it is necessary to spin up a version of RabbitMQ even if only testing part of the full pipeline. We configure to 1M hl7 messages and 100K hoover messages to be queued at any point to avoid loss of disk space when a large amount of messages are being processed. In general this is only likely to apply when we are starting off a run from scratch. The normal day to day running of EMAP should not encounter memory problems. 

 

### Custom code 

 

Our code is written to facilitate creating and submitting batches of messages. Messages are batched by data type until there are three batches ready to be sent to the publisher. Processing is then paused until one batch has been fully acknowledged by the RabbitMQ. Each message is paired with a unique id – unique within the whole RabbitMQ instance to allow precise tracking of messages. Messages are published individually to RabbitMQ.  As each message is published and acknowledged by RabbitMQ it is removed from the batch. This handled by the RabbitMQ callback which is used to determine whether a message has been acknowledged or not and to either remove or resend the message. A second callback  checks for whether a batch is empty and processing of a new batch can begin. 

 

**There is something here about timestamps and updating progress that I'm not sure I understand possibly**


### Filtering 

 

The RabbitMQ can accept a message from the receiver that states that it could not process the message for some reason, usually it has missing information or is known that we cannot process it. At this point RabbitMQ does not resend the message.   