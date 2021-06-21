# Glossary

## A

- **ATOS**
  
	Hospital IT Contractor

- **Audit classes**

	Code used to keep track of hospital data that has been corrected/deleted to allow for a complete trail of changes 
    in an item of data to be preserved.
  
## B

- **Boilerplate code**

	In computer programming, boilerplate code or just boilerplate are sections of code that are repeated in multiple places with little to no variation. 
	

## C

- <a id="caboodle" style="pointer-events: none"><span style="color:black">**Caboodle**</span></a>
  
	Database used by [EPIC](#epic) for reporting purposes. Updated every 24 hours with the data available
    through live streams. More processing makes data more readable than [Clarity](#clarity), another reporting database.

- <a id="Chronicles" style="pointer-events: none"><span style="color:black">**Chronicles**</span></a>
  
	The live data store of the running [Epic application](#epic). Live chronicles is the data you interact with when 
    using Epic. A second copy of the live data is available through [Shadow-Chronicles](#shadowchron).
- <a id="clarity" style="pointer-events: none"><span style="color:black">**Clarity**</span></a>
  	
	
	Database used by [EPIC](#epic) the purpose of reporting. Updated every 24 hours. Holds 
    data that is otherwise not available through any of the other databases, e.g. [Caboodle](#caboodle).
- <a id="csn" style="pointer-events: none"><span style="color:black">**CSN**</span></a> 

	The Contact Serial Number, assigned to a patient on arrival at the hospital, is related to a particular visit. Within [EPIC}(#epic) many interactons are related to the patient via the CSN. Note though that not every patient is assigned
    a CSN. Information relevant to a patient is available through the CSN or [MRN](#mrn) of a patient.

- **Continuous integration** 
	
	An automated test pipeline that runs test code utoatically when code is committed to a
	repository.

- **CRIU**
  
	Clinical Research Informatics Unit.

	A group within the Trust who work on trying to develop the research capability of the hospital.
	
## D

- **Debugging**

	Debugging tries to find where and why a particular, possibly unexpected behaviour occurs. 

- **Docker container**

	A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application.

## E

- **EAV**
  
	Entity Attribute Value is a representation whereby entities are described with attributes, and these attributes are
    then further described with values. For example, a patient could be the entity with an attribute age, which could 
    have the value 56. 
- **ED**  
  
	Emergency Department of a hospital.

- **EHRS**

	Definition

- <a id="emap" style="pointer-events: none"><span style="color:black">**EMAP**</span></a> 
  
	Experimental Medicine Application Platform; collects data from several reporting databases (including [Caboodle](caboodle) and 
    [Clarity](clarity)) and live data streams
- <a id="epic" style="pointer-events: none"><span style="color:black">**EPIC**</span></a>

	Epic systems is one of the largest providers of health information technology. Epic is a complete suite of 
    applications which can cater to all sections of the hospital and can be customised for a particular institute.

## F

-**Foreign Key**

	Definition

## G

- **getter **

	Term used to refer to computer code used to retrieve types of data e.g. a function getName() would be used to 
    retrieve the 'name' piece of data. Counterpart of setter. 

## H

- <a id="hl7" style="pointer-events: none"><span style="color:black">**HL7**</span></a>

	Health Level 7 International is a set of standards for sharing, intergrating, and exchanging electronic healthcare 
	information, e.g. patient or clinical staff information in a hospital. For detailed information see 
    [here](https://www.hl7.org/about/index.cfm?ref=nav).
  
- **Hoover** 

	Is the component of the [EMAP pipeline](#emap) that collects relevant data from both reporting databases 
    [Clarity](#clarity) and [Caboodle](#clarity).

- <a id="hsl" style="pointer-events: none"><span style="color:black">**HSL**</span></a> 
  
	Health Service Laboratories provide the biochemistry and microbiology analysis for the hospital.

## I

- **IDS** 
  
	Immutable Data Store is the database that receives all live [HL7](#hl7) messages being sent by the Epic system. This 
    database is never changed or deleted, and thus holds a record of all live HL7 messages sent since the time point at 
    which [Epic](#epic) was turned on.
  
- **Indexing**

	A database index allows a query to efficiently retrieve data from a database. Indexes are related to specific 
    tables and consist of one or more keys.

## J

- **Join**

	A JOIN clause is used to combine rows from two or more tables, based on a related column between them, e.g. all 
    the lab results for a patient the information for which are kept in different tables in the [USD](#usd) 

## K

- **Key**

	Keys are used to establish and identify relationships between database tables and also to uniquely identify any 
    record or row of data inside a table.

## L

- **Linting**

	Automatic checking of source code for errors and style problems. While there are a lot of tests that can be 
    automated, at the same time there are limitations to these automated checks.

## M

- <a id="mrn" style="pointer-events: none"><span style="color:black">**MRN**</span></a>

	Medical Record Number assigned to a patient arriving in the hospital. Much of the information relating to a patient
    can be retrieved by either the MRN or [CSN](#csn).

## N

## O
	
- **OMOP**
  
	[Observational Medical Outcomes Partnership](https://www.ohdsi.org/omop/) was A public-private partnership 
    established to inform the appropriate use of observational healthcare databases for studying the effects of medical 
    products. Is now superseeded by 
    [Observational Health Data Science and Informatics](https://www.ohdsi.org/data-standardization/the-common-data-model/).
- **OpenEMR**
	
	[OpenEMR](https://github.com/openemr/openemr) is an open source electronic health records and medical practice 
    management solution.
	
## P

- <a id="poc" style="pointer-events: none"><span style="color:black">**POC**</span></a> 
  
	Point Of Care testing; these are tests that can done with results generated at bedside in situ. Examples include 
    basic urin analysis and glucose level monitoring. 

## Q

## R

- **RabbitMQ**
	
	[RabbitMQ](https://www.rabbitmq.com/) is a message-brokering software used in the [EMAP pipeline](#emap) to record 
    data from both the historic databases ([Caboodle](#caboodle) and [Clarity](#clarity)) and the 
    [HL7 message streams](#hl7) to propagate the data correctly chronicled to the [UDS](#uds).
  
- Relationships (database)

## S

- **setter**

	Term used to refer to computer code used to set the value of data e.g. a function setName('my name') would be used to set the 'name' piece of data to the value 'my name'. Opposite of getter.

- **Sharding**

	Is a process of splitting a single database into smaller pieces, e.g. to spread load and therefore increase the 
    response time of the database.

- <a id="shadowchron" style="pointer-events: none"><span style="color:black">**Shadow chronicles**</span></a> 
  
	Shadow chronicles is a second copy (~1-5 seconds behind) which is used to generate reports. Strictly speaking, 
    chronicles is the name of the application used to access this data, but the data itself is also referred to by the 
    name.
  
- <a id="sip" style="pointer-events: none"><span style="color:black">**SIP**</span></a> 
  
	Strategic Integration Platform acts as a central controller for all electronic messages sent within the 
    hospital. It routes messages from various sources ([POC](#poc), [HSL](#hsl), Imaging) to be recorded in the 
    appropriate databases.
  
- <a id="star" style="pointer-events: none"><span style="color:black">**Star**</span></a>

  The [EMAP database](#emap) that contains the processed data and can be queried by users.

## T

## U

- **UCLH**

	[UCL Hospitals NHS Foundation Trust](https://www.uclh.nhs.uk/about-us/who-we-are) oversees a number of different 
    hospitals in London, providing acute and specialist care.

- **Unit tests**
	
	A method by which units of source code are individually tested for errors and corrected if necessary.
  
- <a id="uds" style="pointer-events: none"><span style="color:black">**UDS**</span></a>
	
	This is the storage space for the [Star database](#star).

## V

## W

## X

## Y

## Z

