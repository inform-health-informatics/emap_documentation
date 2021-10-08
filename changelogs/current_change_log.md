# EMAP Release

**Date: YYYY-MM-DD Current changes not released**

---

### Tables changed

Table           | Attributes added | Attributes removed 
:-- |:-- |:--



#### Explanation


### Additional tables

Consult order tables: `consultation_request`, `consultation_type`, `request_answer`.

Answers to Lab Order questions now stored in the `request_answer` table.

####request_answer

**Attributes**

* request_answer_id
* stored_from
* valid_from
* answer
* parent_id
* parent_table
question_id
consultation_request
Attributes

consultation_request_id
stored_from
valid_from
cancelled
closed_due_to_discharge
comments
consult_id
requested_date_time
status_change_time
consultation_type_id
hospital_visit_id
consultation_type
Attributes

consultation_type_id
stored_from
valid_from
code
name


### Deprecated tables


### Changes/fixes

* Consultation orders

---
<!--
## Data sources



### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.2     |
|Emap_interchange       | 2.2     |
|Emap-Core              | 2.2     |
|Inform-DB              | 2.2     |
|Hoover                 | 2.2     |
>