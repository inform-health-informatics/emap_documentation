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
patient_condition      | added_date |
patient_condition      | resolution_date |
patient_condition      | is_deleted |
visit_observation_type | has_visit_observation |
visit_observation_type | is_real_time |


### Changes/fixes

- Adds columns to patient_condition to accommodate problem lists 
- Adds a `has_visit_observation` column to `visit_observation_type` as a flag for whether this type has underlying data
- Adds a `is_real_time` column to `visit_observation_type` as a flag whether the data is being updated in real time

---

## Data sources

- Problem lists


### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.6     |
|Emap_interchange       | 2.6     |
|Emap-Core              | 2.6     |
|Inform-DB              | 2.6     |
|Hoover                 | 2.6     |
