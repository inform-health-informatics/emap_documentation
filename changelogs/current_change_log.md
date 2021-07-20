# EMAP Release

**Date: YYYY-MM-DD  Current non published changes**

---
## Tables changed

| Table           | Attributes added | Attributes removed |
| :-              |:-                |:-                  |
| ***visit_observation_type***   | ***visit_observation_type_id***       | ***visit_observation_type***         |
| ***visit_observation_type***   | ***source_observation_type***       | ***source_application***         |
| ***visit_observation_type***   | ***creation_time*** |  |
| ***visit_observation_type***   | ***description*** |  |
| ***visit_observation_type***   | ***display_name*** |  |
| ***visit_observation_type***   | ***name*** |  |
| ***visit_observation_type***   | ***primary_data_type*** |  |

### Explanation

***visit_observation_type.visit_observation_type*** was renamed to ***visit_observation_type_id*** to maintain consistency in primary key names

***visit_observation_type.source_application*** was renamed to ***source_observation_type*** to be more explicit that it is storing the type of observation (e.g. `flowsheet`)

---

## Additional tables

Infection is recorded in the condition_type and patient_condition tables.

### condition_type

**Attributes**

* condition_type_id
* stored_from
* valid_from
* data_type
* internal_code
* name
* standardised_code
* standardised vocabulary

### patient_condition

**Attributes**

* patient_condition_id
* stored_from
* valid_from
* added_date_time
* classification
* comment
* internal_id
* onset_date
* priority
* resolution_date_time
* status
* condition_type_id
* hospital_visit_id
* mrn_id

SK ===>> Need to add visit_observation _type_audit table as new table

---


## Changes/fixes

* Flowsheet metadata has been added

* Indexes have been added to lab sample question, lab recent orders and lab results

* Birth datetime recorded by ADT messages has been corrected.

* Patient infections have been added

* Copath multiple collection methods have been incoporated

* Bank Manager Profiles are being processed as labs

* WinPath specimen order numbers have been corrected

---

## Data sources

SK ===>> Infections come from ....

## Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.0     |
|Emap_interchange       | 2.0     |
|Emap-Core              | 2.0     |
|Inform-DB              | 2.0     |
|Hoover                 | 2.0     |
