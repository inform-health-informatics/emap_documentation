# Message flow through EMAP pipeline

As detailed in the [technical overview](./Technical_overview_of_EMAP.md), the purpose of the Experimental Medicine
Application Platform (EMAP) is to offer real-time clinical data suitable to analysis, such as the prediction of ICU 
bed occupancy based on current workloads and planned surgeries. This requires the pipeline to consolidate historical
data with live information available through message streams.

There is support for different versions of HL7. 

## Flow of message

Each dedicated stream writes the messages to an HL7 file in sequential order from which the reader retrieves the 
information for further processing.

## Message streams currently available