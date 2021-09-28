# Overview INFORM Github repositories
 
While the "Inform Health Informatics" Github organisation holds a much larger number of Github repositories, currently 
relevant to any developer wanting to contribute to the project are the following. Note that special permissions may be 
required.

| Github repo | Short description | maintainer |
| ----- | ---- | ----|
| [hoover](https://github.com/inform-health-informatics/hoover) | Source code to "hoover" data from hospital databases. Publishes to rabbitMQ queue | Jeremy |
| [db_validation](https://github.com/inform-health-informatics/db_validation) | Contains code to check integrity and consistency of data within EMAP compared to hospital reporting databases. | Aasiyah |
| [Emap-Interchange](https://github.com/inform-health-informatics/Emap-Interchange) | Defines the EMAP Interchange format, which is utilised for a consistent data representation across the different sources. | Jeremy, Stef |
| [Emap-hl7-processor](https://github.com/inform-health-informatics/emap-hl7-processor) | Code to read data from the different HL7 message streams. Publishes message on respective RabbitMQ queue. | Stef |
| [Emap-Core](https://github.com/inform-health-informatics/Emap-Core) | Processing of interchange messages in RabbitMQ queue to update state of the data in user accessible database. | Stef, Anika |
| [Inform-DB](https://github.com/inform-health-informatics/Inform-DB) | Code needed for the user accessible data store. | Stef |