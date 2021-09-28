# Message flow through EMAP pipeline
As detailed in the [technical overview](../Technical_overview_of_EMAP.md), the purpose of the Experimental Medicine
Application Platform (EMAP) is to offer real-time clinical data suitable to analysis, such as the prediction of ICU 
bed occupancy based on current workloads and planned surgeries. This requires the pipeline to consolidate historical
data with live information available through message streams. 

Messages on these message streams contain diverse data, including patient details such as name and medication 
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

The Hoover (cf. Figure 2 in [Technical Overview](../Technical_overview_of_EMAP.md)) runs  queries to extract data from hospital databases.
This can be historic data, or non-live data that is updated in a daily dump. 
This information is parsed into the interchange data format and published to the 
[RabbitMQ](../technologies_used/RabbitMQ.md) databaseExtracts queue.

### From message stream to RabbitMQ

Each message stream available to the project writes messages to the Immutable Data Store (IDS), populating already some
of the metadata and also providing the entire message text in addition to that. The data orignates from EPIC and is 
served by a technical infrastructure built and maintained by ATOS

As only metadata for the message is provided, all relevant information, such as patient identifier or blood cell 
counts for that patient, are still buried inside a message 
structure and text instead of being easily recallable for comparison. See the bottom of the page 
[here](https://www.lyniate.com/knowledge-hub/hl7-oru-message/) for an example of an HL7 message that could be parsed by
the EMAP HL7 reader.

Once the message has been parsed through the hapi library, the HL7 reader convers this to the interchange format for the
specific data type of the data. Only data identified as useful, reliable and required is parsed. Once the data has been parsed into the correct
format, it is published to the HL7 RabbitMQ queue.

### Other data sources

At the moment there are only two supported sources of data. However, due to the use of the interchange format, any content
from any data source that can be parsed into the interchange format can be handled and integrated with the existing data.
It may require some adaptations in the existing pipeline though to ensure data consistency.


## Message streams currently available
- Admission, Discharge, Transfer (ADT)
    - ADT edits
    - pending/scheduled ADT
- Lab orders and Results
    - Winpath (numerical and short-text labs)
    - CoPath (cellular pathology, text reports)
    - Bank Manager profiles (blood type tests)
- Patient infection banners
- Problem lists
- Consultation requests
- Advanced care decisions (DNA, CPR)
- Bank manager transfusions
- Patient notes
- Allergies
