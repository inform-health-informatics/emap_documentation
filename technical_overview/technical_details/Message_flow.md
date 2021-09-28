# Message flow through EMAP pipeline
As detailed in the [technical overview](../Technical_overview_of_EMAP.md), the purpose of the Experimental Medicine
Application Platform (EMAP) is to offer real-time clinical data suitable to analysis, such as the prediction of ICU 
bed occupancy based on current workloads and planned surgeries. This requires the pipeline to consolidate historical
data with live information available through message streams. 

Messages on these message streams hold varying kinds of data, including patient details such as name and medication 
given, but also doctors treating the patient and which ward and bed this patient has been in. 
It should be noted here, that the HL7 Reader in its current version supports different versions of the HL7 messaging 
standard through HAPI. 

The complexity of consolidating data originating from historic database and live streams is amplified by the fact that 
the format of data differs depending on where it originates from. To overcome this limitation, an EMAP interchange data
format has been defined to which all the data is transferred to in order to compare and align it. For further 
information in the exchange format, please take a look [here](Interchange_format.md). 

As not everyone might be familiar with the nature of the data in a hospital setting, additional information on the 
nature of the available data in a hospital can be found [here](../Background_information.md)


## Data from different sources 

To illustrate the process of how data is merged as part of the EMAP pipeline, we have split this section into two parts,
corresponding to historic data and data from messages streams as both are handled through different parts of the 
EMAP pipeline components before being merged. Once all the data is accumulated in 
[RabbitMQ](../technologies_used/RabbitMQ.md), all the data is handled in the same way, independent of the source it 
originally came from.

### From historic database to RabbitMQ

The Hoover (cf. Figure 2 in [Technical Overview](../Technical_overview_of_EMAP.md)) runs detailed queries to receive data 
held in historic database of the hospital wrt. the information about a patient that is relevant, e.g. historic encouters of 
patients with medical staff. This information is then parsed into the interchange data format and written to the
[RabbitMQ](../technologies_used/RabbitMQ.md) handling queue.

### From message stream to RabbitMQ

Each message stream available to the project writes messages in a sequential order to an HL7 file. The HL7 Reader (cf. 
Figure 2 in [Technical Overview](../Technical_overview_of_EMAP.md)) reads the messages from the HL7 file, assigns a 
unique identifier to it and stores the messages "as is" in the Immutable Data Store (IDS). This means that all relevant 
information, such as patient identifier or blood cell counts for that patient, are still buried inside a message 
structure and text instead of being easily recallable for comparison. See the bottom of the page 
[here](https://www.lyniate.com/knowledge-hub/hl7-oru-message/) for an example of an HL7 message that could be parsed by
the EMAP HL7 reader.

Once the message has been parsed through the hapi library, the format of it is changed to the interchange format of the 
specific data type of the data. This means that perhaps not all the data is retained from the HL7 message, only those 
parts that have been identified as reliable and needed for integration. Once the data has been parsed into the correct
format, it is then written to the RabbitMQ handling queue for consolidation into one data source together with all the
other data sources that data is retrieved from.

### Other data sources

At the moment there are only two supported sources of data. However, due to the use of the interchange format, any content
from any data source that can be parsed into the interchange format can be handled and integrated with the existing data.
It may require some adaptations in the existing pipeline though to ensure data consistency.


## Message streams currently available
