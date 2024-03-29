# The Interchange format as basis for data integration

## Background
As detailed in the illustration of the data flow, the EMAP pipeline has the potential to consolidates data from several
sources and more can be added over time as and when necessary. For the moment, the data is provided through two 
main types of sources: 
    
1. incremental load from databases (also referred to as hoovering) and
1. HL7 message streams

Due to the different sources, the data provided to the EMAP pipeline differs in the way it is formatted and it is 
necessary to define a common a structure for the purpose of consolidation. While both the  
[HL7 standard](https://www.hl7.org/implement/standards/) and the [FHIR standard](https://www.hl7.org/fhir/overview.html)
were considered for this purpose, the aim behind both of these standards is that a digital conversation between the 
different technologies used in the hospital can be enabled, but not the integration different data sources 
sources. A custom Interchange format was designed to be less variable and more conducive to data
integration. 


## Key differences between HL7 and Interchange format

The first key difference between both the formats is that all Interchange messages have consistent  use of fields for the 
source of the data. Each of the sources is defined by source system and a source identifier. Using this information, 
we can track the origin of Interchange messages. This information can also be helpful if problems 
occur during message processing and the information needs to be searched for in the 
[Immutable Data Store (IDS)](../../Glossary.md).

The second key difference is that HL7 accumulate multiple changes in one message whereas the Interchange format would
have several messages for the same purpose. For example an HL7 message could have several flowsheet observations in one message. An interchange message is created for each flowsheet on parsing the hl7.

The third key difference is that because HL7 is focussed on digital communication, it is context sensitive, i.e. all 
messages relating to a conversation are needed to determine in which the relevant information has changed. The 
Interchange format, however, is context insensitive, i.e. messages can be handled independent of others and the data
in the user data storage (UDS) updated accordingly.









