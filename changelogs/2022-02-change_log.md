# EMAP Release

**Date: 2022-02-14 Changes in this release**

---

### Tables changed

Table           | Attributes added | Attributes removed 
:-- |:-- |:--
VisitObservation | [sourceSystem](../data_dictionary/tables.md#VisitObservation) |
VisitObservationType | [interfaceId](../data_dictionary/tables.md#VisitObservationType) |sourceSystem


### Explanation

The **VisitObservation** table now includes the ***sourceSystem*** attribute which has been removed from **VisitObservationType** table as the former is a more logical place to locate this data.

The **VisitObservationType** table now includes the ***interfaceId*** attribute as well as the ***idInApplication*** attribute. The original idInApplication attribute is the code used by the source system for the observation type, whereas the interfaceID is the ID used in the hl7 message to refer to this type. Previously a flowsheet that had been added to the live hl7 feed would have two VisitObservationTypes (one from  the hl7 feed and one from caboodle), this change now ensures that the same VisitObservationType is used regardless of the source of the data.



---

### Changes/fixes

* Temporal columns are now all timezone aware, this has been enforced with automated testing of any timezone field
* Hl7 feed only parses new patient infections
* Patient infections that are associated with an encounter have a hospital_visit_id
* Improved speed of load times by updating caching
* Fixes Log4j exploits
* Coded flowsheets are now parsed as the raw id values given in the Hl7 feed

---
<!--
## Data sources



### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.4     |
|Emap_interchange       | 2.4     |
|Emap-Core              | 2.4     |
|Inform-DB              | 2.4     |
|Hoover                 | 2.4     |
>
