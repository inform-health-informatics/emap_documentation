# EMAP Release

**Date: YYYY-MM-DD  Current non published changes**

---
## Tables changed

====>>> SK Note: I couldnt see where this has changed

| Table           | Attributes added | Attributes removed |
| :-              |:-                |:-                  |
| ***visit_observation***   | ***att1***       | ***att2***         |

### Explanation

***visit_observation_type.visit_observation_type*** was renamed to ***visit_observation_type_id*** to maintain consistency in primary key names

***visit_observation_type.source_application*** was renamed to ***source_observation_type*** to be more explicit that it is storing the type of observation (e.g. `flowsheet`)

=====>>> SK Note: I couldnt work out where location and flowsheet metadata is

---

## Additional tables

Infection is recorded in the condition_type, patient_condition and question tables.

====>>> SK Note: I will start on a data dictionary for EMAP and then these could just be links

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

### question

**Attributes**

* question_id
* question

Consult orders are recorded in the consultation_request, consultation_request_answer and consultation_type tables.

### consultation_request

**Attributes**

* consultation_request_id
* stored_from
* valid_from
* cancelled
* closed_due_to_discharge
* comments
* consult_id
* requested_date_time
* status_change_time
* consultation_type_id
* hospital_visit_id

### consultation_request_answer

**Attributes**

* consultation_request_question_id
* stored_from
* valid_from
* answer
* consultation_request_id
* question_id

### consultation_type

**Attributes**

* consultation_type_id
* stored_from
* valid_from
* code
* name

---

## Deprecated tables

### table_gone1

This table is gone because ...

---

## Changes/fixes

* Location metadata has been added

* Flowsheet metadata has been added

* Indexes have been added to lab sample question, lab recent orders and lab results

* Birth datetime recorded by ADT messages has been corrected.

* Consult orders have been added

* Patient infections have been added

* Copath multiple collection methods have been incoporated

* Bank Manager Profiles are being processed as labs

* WinPath specimen order numbers have been corrected

---

## Data sources

Infections come from ....

Consult orders come from live HL7 feed.

## Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.0     |
|Emap_interchange       | 2.0     |
|Emap-Core              | 2.0     |
|Inform-DB              | 2.0     |
|Hoover                 | 2.0     |
