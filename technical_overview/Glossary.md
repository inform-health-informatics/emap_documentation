# Glossary

## A

- <b>ATOS</b>
  
	Hospital IT Contractor

- Audit classes

	Code used to keep track of hospital data that been corrected/deleted to allow for a complete trail of changes in an item of data to be preserved.
  
## B

- Boilerplate code

	In computer programming, boilerplate code or just boilerplate are sections of code that are repeated in multiple places with little to no variation. 
	

## C

- <a id="caboodle" style="pointer-events: none"><span style="color:black"><b>Caboodle</b></span></a>
  
	Database within the hospital, which is used for reporting purposes. Updated every 24 hours with the data available
    through live streams. More recent than [Clarity](#clarity), another reporting database.
- <a id="Chronicles" style="pointer-events: none"><span style="color:black"><b>Chronicles</b></span></a>
  
	The live data store of the running [Epic application](#epic). Live chronicles is the data you interact with when 
    using Epic. Backup data of the live data is available through [Shadow-Chronicles](#shadowchron).
- <a id="clarity" style="pointer-events: none"><span style="color:black"><b> Clarity </b></span></a>
  	
	One of the databases accumulating hospital information for the purpose of reporting. Updated every 24 hours. Holds 
    data that is otherwise not available through any of the other databases, e.g. [Caboodle](#caboodle).
- <a id="csn" style="pointer-events: none"><span style="color:black"><b> CSN </b></span></a> 

	Contact Serial Number, assigned to patients arriving in the hospital. Note though that not every patient is assigned
    a CSN. All the information relevant to a patient is available through the CSN or [MRN](#mrn) of a patient.

- Continuous integration  
	need info
- CRIU

## D

- Debug

	add info

- Docker container

	add info

## E

- <b>EAV</b>
  
	Entity Attribute Value is a representation whereby entities are described with attributes, and these attributes are
    then further described with values. For example, a patient could be the entity with an attribute age, which could 
    have the value 56. 
- <b>ED</b>    

- ED  
  
	Emergency Department
- <a id="emap" style="pointer-events: none"><span style="color:black"><b>EMAP</b></span></a> 
  
	Experimental Medicine Application Platform; collects data from several reporting databases (see Caboodle and 
    Clarity) and live data streams
- <a id="epic" style="pointer-events: none"><span style="color:black"><b>EPIC</b></span></a>

	Epic systems is one of the largest providers of health information technology. Epic is a complete suite of 
    applications which can cater to all sections of the hospital and can be customised for a particular institute.

## F

## G

- getter

	Term used to refer to computer code used to retrieve types of data e.g. a function getName() would be used to retrieve the 'name' piece of data. Opposite of setter. 

## H

- HL7 Health Level 7

	A standard for exchanging information between medical applications.

	
- Hoover (in EMAP pipeline)

- HSL Health Service Laboratories
- <a id="hl7" style="pointer-events: none"><span style="color:black"><b>HL7</b></span></a>

	Health Level 7 International is a set of standards for sharing, intergrating, and exchanging electronic healthcare 
	information, e.g. patient or clinical staff information in a hospital. For detailed information see 
    [here](https://www.hl7.org/about/index.cfm?ref=nav).
  
- <b>Hoover</b> 

	Is the component of the [EMAP pipeline](#emap) that collects relevant data from both reporting databases 
    [Clarity](#clarity) and [Caboodle](#clarity).

- <a id="hsl" style="pointer-events: none"><span style="color:black"><b>HSL</b></span></a> 
  
	Health Service Laboratories provide the biochemistry and microbiology analysis for the hospital.

## I

- <b>IDS</b> 
  
	Immutable Data Store is the database that receives all live [HL7](#hl7) messages being sent by the Epic system. This 
    database is never changed or deleted, and thus holds a record of all live HL7 messages sent since the time point at 
    which [Epic](#epic) was turned on.
  
- <b>Indexing</b>

	A database index allows a query to efficiently retrieve data from a database. Indexes are related to specific 
    tables and consist of one or more keys.

## J

- <b>Join</b>

	A JOIN clause is used to combine rows from two or more tables, based on a related column between them, e.g. all 
    the lab results for a patient the information for which are kept in different tables in the [USD](#usd) 

## K

- <b>Key</b>

	Keys are used to establish and identify relationships between database tables and also to uniquely identify any 
    record or row of data inside a table.

## L

- Linting

	Need info

## M

- <a id="mrn" style="pointer-events: none"><span style="color:black"><b>MRN</b></span></a>

	Medical Record Number assigned to a patient arriving in the hospital. Much of the information relating to a patient
    can be retrieved by either the MRN or [CSN](#csn).

## N

## O

- OMOP Observational Medical Outcomes Partnership

	A public-private partnership established to inform the appropriate use of observational healthcare databases for studying the effects of medical products.
- OpenEMR

	An open source electronic health records and medical practice management solution.

- <b>OMOP</b>
  
	[Observational Medical Outcomes Partnership](https://www.ohdsi.org/omop/) was a public-private partnership to inform
    the appropriate use of healthcare databases. Is now superseeded by 
    [Observational Health Data Science and Informatics](https://www.ohdsi.org/data-standardization/the-common-data-model/).
- <b>OpenEMR</b>
	
	[OpenEMR](https://github.com/openemr/openemr) is an open source medical management software.
	
## P

- <a id="poc" style="pointer-events: none"><span style="color:black"><b>POC</b></span></a> 
  
	Point Of Care testing; these are tests that can done with results generated at bedside in situ. Examples include 
    basic urin analysis and glucose level monitoring. 

## Q

## R

- <b>RabbitMQ</b>
	
	[RabbitMQ](https://www.rabbitmq.com/) is a message-brokering software used in the [EMAP pipeline](#emap) to record 
    data from both the historic databases ([Caboodle](#caboodle) and [Clarity](#clarity)) and the 
    [HL7 message streams](#hl7) to propagate the data correctly chronicled to the [UDS](#uds).
  
- Relationships (database)

## S

- setter

	Term used to refer to computer code used to set the value of data e.g. a function setName('my name') would be used to set the 'name' piece of data to the value 'my name'. Opposite of getter.

- Sharding

	need info

- <a id="shadowchron" style="pointer-events: none"><span style="color:black"><b>Shadow chronicles</b></span></a> 
  
	Shadow chronicles is a second copy (~1-5 seconds behind) which is used to generate reports. Strictly speaking, 
    chronicles is the name of the application used to access this data, but the data itself is also referred to by the 
    name.
  
- <a id="sip" style="pointer-events: none"><span style="color:black"><b>SIP</b></span></a> 
  
	Strategic Integration Platform acts as a central controller for all electronic messages sent within the 
    hospital. It routes messages from various sources ([POC](#poc), [HSL](#hsl), Imaging) to be recorded in the 
    appropriate databases.
  
- <a id="star" style="pointer-events: none"><span style="color:black"><b>Star</b></span></a>

  The EMAP database that contains the processed data and can be queried by users.

	Refers to a schema and library applied to the [UDS](#uds) through which the almost real-time data of the hospital is
    available. The schema allows a consistent representation of the data from the different hospital databases and live
    streams and enables comparison.
  
## T

## U

- <b>UCLH</b>

	[UCL Hospitals NHS Foundation Trust](https://www.uclh.nhs.uk/about-us/who-we-are) oversees a number of different 
    hospitals in London, providing acute and specialist care.

	

- Unit tests
- <a id="uds" style="pointer-events: none"><span style="color:black"><b>UDS</b></span></a>
	
	This is the storage space for the  [Star database](#star).

## V

## W

## X

## Y

## Z

