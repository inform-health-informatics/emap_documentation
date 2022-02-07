# EMAP Release

**Date: 2022-02-07 Changes in this release**

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
