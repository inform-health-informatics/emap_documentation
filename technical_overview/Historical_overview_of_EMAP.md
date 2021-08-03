# Historical Perspective

## Before the INFORM project

Originally there was a Health Informatics Collaborative (HIC) project which involved 5 NHS trusts who all sent data to the UCL data safe haven.
The data, which only involved  [ICU](../Glossary.md##I) data, was in an XML HIC format.
The UCL Research Software Development Group [(RSDG)](https://www.ucl.ac.uk/isd/services/research-it/research-software-development) did some work on processing these files.

## Starting INFORM

Recognising the value of having data in a research format, a number of ICU consultants acquired funding to develop a pipeline that would produce data in a format that would facilitate research and dashboards that could be accessed in real time and continued to collaborate with RSDG to accomplish this.

At this time (2018 - early 2019) the hospital had hundreds of systems and so the goal was to build a research database that took data from all of these systems.
During the first year of the project a system was created that did an [ETL](../Glossary.md#E) of ICIP, the EHRS (Electronic Health Record System) for the ICU.
Since the ETL happened every 15-minutes this allowed us to read ISIP and create a pipeline that powered a dashboard on top that was essentially real time.

## and then came EPIC

In April 2019, many of the hospital systems were replaced by [EPIC](../Glossary.md##E), a centralised system that started to make the entry and storage of data more consistent and produced a small number of centralised databases to replace the large variety of inconsistent systems and databases being used within the Trust at that time.

ISIP was turned off and the focus of the INFORM project moved to reading the [hl7 stream](../Glossary.md#H), the commnication format used by the EPIC infrastructure, and formatting the data into a standard database representation.
Initially this focused on [OMOP](../Glossary.md##O) as this was an existing standard.
However, we quickly realised that since OMOP is specifically non-live, anonymised data, it woud not serve the intended purpose.
So we created our own schema emap star and a pipeline that would process live HL7 data into star and from there process the data into OMOP.

## EMAP Star

### Version 1

When EMAP Star was designed, it was designed with flexibility in mind and used an [Entity Attribute Value](../Glossary.md##E) approach to make it easily extensible.
By December 2019, we had a working version of the pipeline that stored [ADT data](../Glossary.md##A) and some [Flowsheets](../Glossary.md##F).
However this proved difficult to query, particularly needing unintuitive, low performance joins.
As more data was added we also realised that the size would become problematic and ultimately unscalable.

### Refactored

So we redesigned based on a structured data set with wide tables to allow us to store the information we were receiving.
The benefits of wide tables are that the format can be changed as needed, the data is predicatable as it has a defined structure and it easy to add indexes to further facilitate performant queries.

The refactoring was undertaken in stages, with user demonstrations given at each stage. This allowed us to incorporate feedback as the refactoring progressed. The newly refactored Star went live in March 2021. At this point, we incorporated ADT, Flowsheets, Demographics and Lab results.

## Pipeline

### Codebase

Java was chosen for the code base for several reasons

- ATOS, the hospital IT contractor who support the project infratructure inside the hospital use Java
- Java is a well stablished enterprise grade software
- the strong typing and use of boilerplates made it conducive to the project requirements
- and Roma insisted

### Microservices

The choice to create the pipeline as a series of microservices was to contain complexity.
The complexity of each element is small compared to the complexity of the overall system and the use of RabbitMQ hugely facilitates this as it is good at buffering messages.
It has never been a project requirement that we should be able to release an old version of the software.
So therefore having several microservices and maintaining different repositories for each facilitates maintaining the pipeline such that the latest release of each of the microservices work together and we make no effort to be in anyway backwards compatible.

### Multithreading

We have considered multi-threaded loading of the data.
However this would involve locking certain data as information about the same record maybe being received by more than one thread.
We also falsely assumed that messages would come in order.
This is not the case and we have had to put a lot of code in to rectify the incorrect data that gets stored if messages are received out of order.
Given the combined issues of locking and out of order messages it was decided that our load time is fast enough at this stage to not warrant multithreading.
For now we are going with competency rather than concurrency as it is safer.
Also, given the current location of EMAP on a shared GAE we are unlikely to get a particularly optimised performance.
In a couple of years time when we have hugely increased amount of back data and a large number of data points coming in daily we may well need to readdress performance.

### Deprecation of OMOP

In March 2020, with the advent of Covid, our manpower and focus shifted and at this stage it was decided to stop persuing the OMOP ETL.
At this point (August 2021) is is unlikely that the project will revitalise this aspect.
