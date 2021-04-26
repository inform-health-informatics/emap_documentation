# Message flow through EMAP pipeline
As detailed in the [technical overview](./Technical_overview_of_EMAP.md), the purpose of the Experimental Medicine
Application Platform (EMAP) is to offer real-time clinical data suitable to analysis, such as the prediction of ICU 
bed occupancy based on current workloads and planned surgeries. This requires the pipeline to consolidate historical
data with live information available through message streams. 

Messages on these message streams hold varying kinds of data, including patient details such as name and medication 
given, but also GPs treating the patient and which ward and bed this patient has been in. 
It should be noted here, that the HL7 Reader in its current version supports different versions of the HL7 messaging 
standard through HAPI. 

The complexity of consolidating data originating from historic database and live streams is amplified by the fact that 
the format of data differs depending on where it originates from. To overcome this limitation, an EMAP interchange data
format has been defined to which all the data is transferred to in order to compare and align it. For further 
information in the exchange format, please take a look [here](./Interchange_format.md). 


## Two different data flows
To illustrate the process of how data is merged as part of the EMAP pipeline, we have split this section into two parts,
corresponding to historic data and data from messages streams as the both are handled through different parts of the 
EMAP pipeline components before being merged.

### From historic database to data consolidation

Hoover abstracting data from databases

### From message stream to data consolidation

Each message stream available to the project writes messages in a sequential order to an HL7 file. The HL7 Reader (cf. 
Figure 2 in [Technical Overview](./Technical_overview_of_EMAP.md)) reads the messages from the HL7 file, assigns a 
unique identifier to it and stores the messages "as is" in the Immutable Data Store (IDS). This means that all relevant 
information, such as patient identifier or blood cell counts for that patient, are still buried inside a message 
structure and text instead of being easily recallable for comparison. See the bottom of the page 
[here](https://www.lyniate.com/knowledge-hub/hl7-oru-message/) for an example of an HL7 message that could be parsed by
the EMAP HL7 reader.

After the message has been written to the IDS, it is transformed into a flowsheet, the internal EMAP interchange format.
A single flowsheet or a batch of flowsheets is then added into a queue for further processing. 




## Message streams currently available

