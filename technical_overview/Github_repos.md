# Overview INFORM Github repositories
 
While the "Inform Health Informatics" Github organisation holds a much larger numbe of Github repositories, currently 
relevant to any developer wanting to contribute to the project are the following. 

| Github repo | Short description | maintainer |
| ----- | ---- | ----|
| hoover | Source code to "hoover" data from the historic database in the hospital | Jeremy |
| db_validation | Contains code to check integrity and consistency of data across the different databases of the EMAP pipeline. | Aasiyah |
| Emap-Interchange | Defines the EMAP Interchange format, which is utilised for a consistent data representation across the different sources. | Jeremy, Stef |
| Emap-hl7-processor | Code to read data from the different HL7 message streams. Publishes message on respective RabbitMQ queue. | Stef |
| Emap-Core | Processing of interchange messages in RabbitMQ queue to update state of the data in user accessible database. | Stef |
| Inform-DB | Code needed for the user accessible data store. | Stef |