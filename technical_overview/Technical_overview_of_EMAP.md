# Technical Overview EMAP

[//]: #1 (I should probably know this by now, but is EMAP an abbreviation of some sort?)

## Introduction

Data and metadata are an integral part of any hospital’s electronic information systems. In hospital systems data is 
recorded in a variety of locations depending on the needs of the administrative and clinical staff.  Data can also come in many forms, it may be plain text, images and even on occasions pdfs. Metadata relates the concept being recorded to internal mapping or external ontology records. The core system, 
which records most data, is not suitable for general reporting and so secondary data sources are automatically created, 
as bulk loads. In UCLH the data is consolidated during a nightly process of automated batch loads that creates multiple 
databases (Caboodle/Clarity in Figure 1) tailored for hospital reporting. While this data can be used for research, 
the nightly consolidation process means that the databases are always behind what is currently happening and may not 
exactly match events as they occurred. 




[//]: #2 (Again, this might be me not knowing better, but what is the "core system" and why is it not suitable for 
"general reporting"? I guess that could be added a little more detail in half a sentence or so)

![Data flow in the hospital](./images/Figure_1.png)

[//]: #3 (If I were to polish this figure, I would probably aim to have the labels not run over arrows if possible. What 
is Chronicles, POC, SIP and HSL? Could that perhaps be added in the label? I notice that a clinician might know these 
acronyms and some are mentioned in the text going forward, but I guess if the reader is already directed here it might
help adding the information to the label?)

In order to provide live data suitable for research and clinical applications we have created EMAP, a pipeline that 
includes both gathering data in real-time and retrieving historical data; functionality not mirrored by any other 
accessible database within the Hospital Trust. The database is structured in a logically modelled fashion to allow easy 
access. Data targeted by EMAP is data that has been specifically identified as useful to individual researchers 
requesting access. Providing these users with the relevant data outside of the hospital operational systems lowers the 
load on these systems. As a non-operational database it allows provision for long, slow queries without risking impact 
on the hospital systems. The resulting database can be used, for example, by a researcher creating a predictive model 
of whether a patient presenting in ED is likely to be admitted to the main hospital, or by a technically inspired 
clinician to create an up-to-date view of derived metrics of each patient in a given ward. 

[//]: #4 (I'm not sure that I know what is meant by "logically modelled" and could benefit from a bit of additional info
or rephrase here)

[//]: #5 (This might be because I'm not a native speaker, but "individual researchers" made it sound that EMAP is 
something "nice to have" rather than something crucial to have, which might be fine. I guess if I wanted to stretch the 
importance of the system, I'd lead with the stats on a ward for the clinician and then mention that this data is also 
useful for research projects. The other way is leading with hospitals are set to transform and active research is 
necessary to make data fit for purpose so that it can be used going forward to inform decision making)

[//]: #6 (There might be a confusion in my mind, but I guess "slow queries" makes me wonder how slow "slow" is. The 
struggle I have -- and this might be rooted in a misunderstanding -- is that I thought that one benefit of EMAP was to
have data available much faster and it somehow contracts the "slow queries". I appreciate that there is a difference
between gathering and querying, but maybe there is a little more info that could be added here to clarify this?)

![EMAP pipeline](./images/Figure_2.png)

[//]: #7 (Later on this document mentions that laptops symbolise code in this figure and for consistency I'd be tempted
to add it to the label here too. Somebody may think there is hardware and software here?)

## Pipeline

Streams of messages within the hospital are published to the SIP (Strategic Integration Platform) which routes these to 
one or more consumers. For the purposes of EMAP, a subset of messages from a subset of these streams are copied to a 
dedicated PostgreSQL database that assigns a unique ID to each message and creates a copy of the message as-is in the 
database as well as creating columns for common message data fields, e.g. PatientName. This database, the 'IDS' 
(Immutable Data Store) in Figure 2, provides a backup of all live messages that have been transmitted to it from the 
point when any given feed went live. This has proved invaluable to development of the pipeline and resulting database 
as it provides an increasing set of test data with which to optimize the workflow and resulting database schema. 
As more live message streams have been added, we have been able to identify and fix issues that may occur with 
out-of-order, duplicate or indeed missing messages. This step in the pipeline is facilitated by ATOS (hospital 
IT contractor) with whom we have a good working relationship for resolving issues that arise. 

[//]: #8 (What are "streams of messages" used for in the hospital, e.g. notify a clinician about something or do the 
messages have more details than that? When does a new stream become available and how will those be integrated into 
EMAP? I guess I'm wondering about governance going forward: if I'm a researcher that needs a new stream, whom do I ask
for that to be added; does that work automatically? How do these message streams relate to the information in the 
Caboodle/Clarity databases?) 

The Hoover code is written to allow incremental loading from any of the databases within the hospital system, running 
different queries against different databases as required. Since the instance and type of database may vary, the service 
has been designed to abstract the processing of data, only requiring classes that define the database connections, 
querying the database and converting that into a set of messages using our in-house interchange format. 

[//]: #9 (How are these databases different from the "core system" and the EMAP database -- is that perhaps the 
historical clinical data? Why was it necessary to introduce an "in-house interchange format"? It's the first time 
it's mentioned here and could benefit from a little more detail)

Message types within the hospital go ‘live’ at different points depending on when that interface was configured to send 
to EMAP. Thus, in order to provide access to all data for a particular feed, we also use the Hoover instances to 
provide data that pre-dates the live status or complements these with types of data that are not yet live.   
 
The HL7 Reader processes the live messages as they appear in the IDS. HL7 (Health Level Seven) is a standard for 
exchanging information between medical applications. An HL7 message consists of one or more segments. Each segment 
consists of one or more composites, also known as fields. The HL7 Reader parses the HL7 message, identifies the 
segments of interest and extracts the relevant fields. It should be noted that although HL7 is a standard, messages 
sent within a hospital can be customised by the system administrators. Thus, the HL7 parsing aspect of our pipeline 
needs to be tailored for each system and message stream being read. 
 
Data processed by the HL7 Reader also results in messages formatted in our in-house interchange format. This allows 
for the pipeline to deal with similar data coming from different sources in an identical fashion. The interchange 
format is coded as a Java package, involving a set of Serializable Java classes, serialised test messages for 
integration and system testing and helper methods for testing. The format has been designed to formalise custom 
HL7 implementation semantics into use-specific fields, allowing the processing of these messages downstream to be 
ignorant of HL7. This standardisation step also allows the interchange format to be readily included in any code 
involving data sources or destinations. 

[//]: #10 (Still not quite clear as to why a separate format is needed. Couldn't all the data have been formatted as HL7?)
 
Messages, in the interchange format, are batched and sent to the appropriate queue managed by the RabbitMQ server. 
Priority is given to messages originating with the live stream. Each queue has a maximum number of messages that are 
allowed, and the services publishing to the queues implement an exponential backoff policy to limit the amount of disk 
space used by the queues.  

[//]: #11 (It might be good to add info that there's more detail on RabbitMQ to come; why is priority given to messages 
from live streams? Is there any instance where this might be a false assumption to make because of approval not yet 
been through or something? thinking here about GP who gets e.g. blood results and while these results are flagged, a GP
still goes manually through them before the result is given to you. Would it be helpful to add a short explanation for 
what a queue is and why it is needed?)
 
The event processor receives messages in the interchange format from RabbitMQ. Each message is received and processed 
individually before data is added into the ‘star schema’ of the UDS (User Data Store) (see Figure 3). 

We maintain two instances of the star schema with views created for the current active instance. This allows us to 
update code, perform fixes and add additional feeds without requiring downtime and disruption to users.

[//]: #12 (is this really instance of the schema as opposed to data stored in schema?)

Data being added to the database must be checked to ensure that references to the same patient or the same hospital 
visit are correctly recorded. Patients arriving at the hospital are allocated an MRN (medical record number) and in 
some cases a CSN (contact serial number, or visit number, denoted Hospital Visit in Figure 3). Much of the information 
within the database is linked to these two numbers, or an NHS number on the occasion where there is no MRN or CSN 
available. Some things, such as Lab reports, have their own identifiers and our processing enables these to be related 
to the appropriate patient. 

![Schema for the EMAP ‘star’ database stored on the UDS](./images/Figure_3.png)

Messages being processed by the EventProcessor must also allow for changes in existing information. For example, a 
patient can be inadvertently assigned to different MRNs, and once this has been detected the records for each need to 
be merged. EMAP creates an audit table (not shown) to mirror each table that can have meaningful changes, into which 
information that has been updated or deleted is recorded. This facilitates distinguishing valid data from invalid data 
(the star schema always contains the latest values), whilst providing an audit history for any changed information.

[//]: #13 ("assigned to different MRNs" -- is this meant to be "two" instead of "to"? is two the upper limit or can there 
be more than that? One thought that occurred at this point is, what happens when a new live stream is added that holds
data that does not exist in UDS, does it time-wise backfill this information or is it only available from the time the 
stream is added?)

Entries are also made in the star database to record the last message processed with the corresponding timestamp. 
This allows maintainers of the database to check progress and establish the timeframe of missing data should any of 
the pipeline or hospital infrastructure feeding it have suffered a period of outage. It also allows the HL7 Reader to 
restart in the event of a crash or system failure, since it has persistent state.

[//]: #14 (Depending on audience, I might be tempted to replace "feeding it" with something like "no messages available" 
available or something)

## Star schema
 
Most schemas for healthcare data are proprietary e.g. EPIC. Open source schemas tend to be for data transfer. We 
nevertheless reviewed existing options. OpenEMR is a popular open source electronic health records and medical 
practice management solution. However this standard is vast, and includes large amounts of data that are not of 
interest for EMAP. The OMOP format provides an anonymous, fixed version of patient record data. However, the user 
requirements for EMAP included demographics and time 'aware' information which could not be provided by using the 
OMOP standard without significant changes. OMOP is also not suited to live data. We concluded that we would need to 
devise our own schema.

[//]: #15 (I might have the wrong end of the stick, but "solution" in my mind is not the same as schema; the way it's 
phrased currently, I wonder whether someone would understand it to be the same though)

Initially we looked at an entity-attribute-value approach for maximum flexibility. This did allow easy addition of 
different types of data but caused major usability issues for alpha users, with slow indexing and complex joins. 
Technical evaluation and the learning process involved in creating the pipeline showed that the flexibility provided 
was unnecessary, and thus we undertook a redesign that separated the data into clearly distinct individual tables as 
shown in Figure 3. This has proved popular with our users and feedback confirms it is faster and more intuitive than 
the generic approach.

[//]: #16 (is everyone in the audience of this document aware what an entity-attribute-value approach is? If not it might 
be helpful to add a little explanation for it. Not sure whether that is best done as a figure or so. Similarly, can we
expect that everyone reading this document knows what indexing is and joining, with reference to data that is?) 

## Technologies used 

The code written for the EMAP pipeline consists of a number of Java packages denoted by the laptop icon in Figure 2. 
We have used the following technologies and frameworks.

[//]: #17 (I personally would probably add a summary of what is all there first before going into detail of each. At the 
moment the transitions happen quite abruptly and I wonder whether someone less familiar with technology would take well
to "jumping". Something like "The EMAP infrastructure includes, RabbitMQ scheduling, PostGres databases, ... and we'll 
now proceed to explain these technologies further.")

RabbitMQ was chosen for channeling messages as it provides robust hardiness against failure, which can be configured to 
best suit the system. We have configured the message streams to be received as batches and processed individually. The 
configuration also allows us to determine whether a message is processed “at least once” or “at most once”. Our 
priority is that we capture all data and so the potential data loss of the “at most once” approach would not be 
suitable.

[//]: #18 (Reading up to this point, I'm still a little unsure why a queuing system is needed in the first place. 
Couldn't I just make records as they appear in one long list? why would a message be processed more than once?)

Using the "at least once" option is implemented by RabbitMQ by delivering the message to the client, and flagging it. 
It isn't marked as delivered until it is ‘acked’ by the client application, which only happens when processing is 
complete. Failing to receive an ack means that the message is resent, ensuring each message is received. In the event 
of a failure between finishing processing and the ack being sent, the message would be sent again allowing for 
redundancy in the presence of failures, which may cause duplicate processing. Using this configuration option required 
investing time in making sure that such duplicate messages don't lead to duplicated data in the UDS. Conveniently for 
us, this handling of duplicate messages is needed not just to account for possible failure scenarios within our own 
RabbitMQ pipeline, but also to track duplicate "source" messages that we receive in cases of an upstream failure 
recovery.

[//]: #19 (can we safely assume that every reader knows what a "client" is? "acked" I assume is acknowledged? In terms 
of ordering, I'd probably move this paragraph before the one before so that there is an explanation of how the hospital 
system operates in itself and how EMAP complements it with RabbitMQ)

Our RabbitMQ is also configured to backup running queues to disk. This avoids data loss in the case of a RabbitMQ 
failure. This does have some minor performance implications but these were deemed small enough to be negligible in our 
case. Since we know the general size of messages being sent we mitigated the use of disk space by configuring length 
limits on our queues. We have abstracted away the interaction with RabbitMQ in the code into a shared library that we 
use to ensure that bug fixes in the interaction are propagated to all applications.

[//]: #20 (The above paragraph is slightly confusing to me, but this may be due to my limited of RabbitMQ. While RabbitMQ
is running, it's generating back-ups of it active queues, that I follow. However, when it has a failure does it still 
continue to record occurring message and backing them up -- I would have expected it to stop recording and therefore 
incur a loss of messages that would have needed to be written to the queues while there was a failure.)

Libraries and frameworks generally reduce code by virtue of providing specialist functionality. The Spring framework 
has components for databases, RabbitMQ (AMQP) and scheduling and so fitted our use of standard enterprise software. 
Hibernate provides the perfect partner for Spring with database interaction. Lombok has allowed streamlining of data 
classes, reducing the amount of boilerplate code required to create getters, setters and equals methods, although we 
did write our own bespoke annotation processor to generate audit classes for the database.

[//]: #21 (do we expect that intended readers of this document know what data classes, boilerplate code, getters, setters,
equals methods, annotations and audit classes are?)

We used PostgreSQL as it is a widely used relational database implementation which is a good match for the UDS. It 
could be argued that Cassandra, which has first class sharding to handle the ever growing volume, would be a better 
fit for the IDS, since it is a stream database with no relationships. However, we relied on the infrastructure that 
could be supported via the hospital IT and contractors so it was deemed more pragmatic that both databases use 
PostgreSQL initially.

[//]: #22 (Do all the intended readers know what "relationships" in a database sense are? Some may equate this to foreign
keys ... )

Internally we use Glowroot, an Open source Java Application Performance Monitor that allows us to monitor the 
performance of the pipeline. It allows tracing slow requests, errors and transaction times as well as supporting 
monitoring of SQL capture and aggregation. Each microservice has a Glowroot instance attached, allowing precise 
monitoring of each aspect individually.

[//]: #23 (Microservice was not used before and I wonder it is easy to make the connection that these are the parts of 
the pipeline. I guess I would aim for consistency and if this is a term that should be included already start 
introducing it very early on and use it throughout the entire document)

We use Docker containers to build and deploy the services that constitute the pipeline. This greatly facilitates 
development, as we can deploy containers based on different branches of code to test new features or debug specific 
issues. 

[//]: #24 (Do all intended readers know what "Docker containers" are and what is meant by "debugging issues"?)

## Testing and validating data

The ethos of the EMAP Development Team is that we produce high quality, well-tested applications. To this end, all of 
our code has low-level unit testing employing the JUnit testing framework. Code is managed using git repositories 
which are set up to run both linting and the suite of unit tests as part of the continuous integration cycle. All code 
is peer reviewed and must be approved by a non-author before it can be fully merged into the relevant code base. 

[//]: #25 (Do we expect that every reader knows what linting, unit tests and continuous integration are?)

As each element of our pipeline is written as a separate microservice, dummy input tests are also written for each 
element to test that the output from each is as expected. 

[//]: #26 (Do we expect that every reader knows what "dummy input tests" are?)

As part of our testing we also create a set of permutation tests of fake messages that allow us to test the pipeline 
for the random receipt of messages.  It is not unknown for us to receive a cancel message before we receive the actual 
message from the live feed, and running all possible permutations of batches of 5-7 messages for different situations 
with defined final states in the database allows us to ensure that the service is robust to duplicate and out-of-order 
messages.

[//]: #27 (Reading this paragraph makes me think that instead of specific messages that are relevant to the information 
we are after, we're instead waiting for a specific sequence of messages. If this is the case, I personally would add
this earlier on; then the notion of a queuing system would make also more sense)

In order to establish the validity of the data being stored in the EMAP star database we have created an R package to 
query data from both star and hospital databases and perform comparisons. These comparisons allow us to quickly identify 
when an entry in star is problematic and provide us with explicit examples with which to debug the processing code. It 
has also allowed us to identify anomalies within the data held in hospital databases. Since the hospital databases do 
not receive live messages they reconcile dates that may have appeared out of order within the live feed. This will 
prevent data in star, derived using only information provided by the live feed, from exact matching with the reconciled 
databases. These mis-matches can be made available to users, enabling them to determine which data is most suitable for 
their particular purpose.

[//]: #28 (What is the EMAP star database? In my mind schema and database are not the same. I had the feeling that it is
the UDS that we are talking about here?)

Besides automated testing and data comparison, we do manually check random entries in the star database with official 
hospital records to verify that the data in star is an accurate representation of the records.

[//]: # (See previous comment)
 
## Storage and Access control 

The IDS has 840 GB of storage of which 76 GB is currently used. As more live HL7 streams and other forms of live data 
export to the IDS are turned on the amount of data will obviously increase. Current prognosis is that we have enough 
space for 22 years worth of data; although this is difficult to accurately project without more detailed analysis.

[//]: #29 (This triggered the thought whether IDS is cleared as things arrive in USD or is there basically a duplicate 
record between IDS and UDS?)

The UDS has 1.5 terabytes of storage of which 279 GB is currently used. At present the star schema and a number of 
development/test schemas used by the development team are not the only databases hosted on the UDS. Users can create 
their own schemas. Ultimately the star schema will need to have priority in the space as more and more data is added 
and options such as sharding will need to be considered.

[//]: #30 (In my mind a schema is not the same as a database rather a database adhering to a schema; does every potential
reader know what "sharding" is?)

At present potential users must apply for access to any individual schema on UDS.  Schemas can be set up specifically 
for projects and users can add their own data, but can also be provided access to either the general research database 
(with a read only permission) or with a special schema that contains only a subset of the full database as appropriate. 
Users can further restrict access to their own data tables to only specific users if they so desire, but the default 
behaviour is that all members of a schema can read all data in that schema. We anticipate creating a more formal 
process in the future. 



