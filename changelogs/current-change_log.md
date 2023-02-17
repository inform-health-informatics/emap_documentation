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
advance_decision |  | mrn_id
lab_battery |  | description
patient_condition      | added_date |
patient_condition      | resolution_date |
patient_condition      | is_deleted |
patient_condition      | severity |
mrn | research_opt_out | 
visit_observation_type | has_visit_observation |
visit_observation_type | is_real_time |


### Changes/fixes

- As each `advanced_decision` always has a hospital visit, removed unnecessary `mrn_id` column
- CoPath lab battery is now populated, rather than using `CO_PATH` for all results
- Remove unused `description` column from `lab_battery`
- Adds columns to patient_condition to accommodate problem lists 
- You can now know if a visit observation type has any data (`has_visit_observation` column) and if it is being updated in real time (`is_real_time` column)
- A patient can now be opted out of research with the `research_opt_out` column

---

## Data sources

- Allergies
- PACS imaging reports. Results added
- Problem lists


### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.6     |
|Emap_interchange       | 2.6     |
|Emap-Core              | 2.6     |
|Inform-DB              | 2.6     |
|Hoover                 | 2.6     |
