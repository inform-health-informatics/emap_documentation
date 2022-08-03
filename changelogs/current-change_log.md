# EMAP Release

**Date: __TODO: FIXME__ Changes in this release**

---

### Tables added

#### ConditionVisits

Linker table for the many-to-many relationship between problem lists and hospital visits.


| Name               | Type | Description                                                                             |
|--------------------| --- |-----------------------------------------------------------------------------------------|
| condition_visit_id | bigint | Unique identifier in EMAP for this ConditionVisit record.                               |
| hospital_visit_id | bigint | Unique identifier in EMAP for the hospital visit (primary key in hospital_visit).       |
| patient_condition_id | bigint | Unique identifier in EMAP for the patient condition (primary key in patient_condition). |

### Tables changed

Table           | Attributes added | Attributes removed | 
:-- |:-- |:--
patient_condition     | added_date |
patient_condition     | resolution_date |
patient_condition     | is_deleted |


### Changes/fixes

---
<!--
## Data sources



### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.6     |
|Emap_interchange       | 2.6     |
|Emap-Core              | 2.6     |
|Inform-DB              | 2.6     |
|Hoover                 | 2.6     |
>
