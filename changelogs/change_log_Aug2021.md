# EMAP Release

**Date: 2021-08-10  Changes in this release**

---

## Data Dictionary

We have started to create a data dictionary with details of the star database. Preliminary version is available [here](../data_dictionary/star_data.md).

---
## Tables changed

| Table           | Attributes added | Attributes removed |
| :-              |:-                |:-                  |
| ***visit_observation_type***   | ***visit_observation_type_id***       | ***visit_observation_type***         |
| ***visit_observation_type***   | ***source_observation_type***       | ***source_application***         |
| ***visit_observation_type***   | ***creation_time*** |  |
| ***visit_observation_type***   | ***description*** |  |
| ***visit_observation_type***   | ***display_name*** |  |
| ***visit_observation_type***   | ***name*** | *** name_in_application*** |

### Explanation

***visit_observation_type.visit_observation_type*** was renamed to ***visit_observation_type_id*** to maintain consistency in primary key names

***visit_observation_type.source_application*** was renamed to ***source_observation_type*** to be more explicit that it is storing the type of observation (e.g. `flowsheet`)

*** visit_observation_type.name_in_application *** was renamed to ***name*** 

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

### visit_observation_type_audit

An audit table to track changes in visit_observtion_type records has been included.

---

## Changes/fixes

* Flowsheet metadata has been added 🆕

* Indexes have been added to lab sample question, lab orders and lab results

* Birth datetime recorded by ADT messages has been corrected.

* Patient infections have been added 🆕

* Copath multiple collection methods have been incoporated

---

## Data sources

Minimal infection data (with no internal ID) comes from hl7, these are overridden by the full extract from Clarity.

<!-- for Internal record>
## Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.1     |
|Emap_interchange       | 2.1     |
|Emap-Core              | 2.1     |
|Inform-DB              | 2.1     |
|Hoover                 | 2.1     |
-->
