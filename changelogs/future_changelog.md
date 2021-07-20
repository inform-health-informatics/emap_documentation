
## Additional tables

Consult orders are recorded in the consultation_request, consultation_request_answer (and question) and consultation_type tables.

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

## Changes/fixes

* Location metadata has been added

* Consult orders have been added

---

## Data sources

Consult orders come from live HL7 feed.

## Repository Versions
