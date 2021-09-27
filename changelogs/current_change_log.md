# EMAP Release

**Date: YYYY-MM-DD  Current non published changes**

---

### Tables changed

Table           | Attributes added | Attributes removed 
:-- |:-- |:--
Location | department_id |  
Location | room_id |  
Location | bed_id |  


#### Explanation

Allows mapping of Hl7 location strings to real-world locations at the department, room and bed level.

### Additional tables

Location metadata tables: `location`, `department`, `department_state`, 
`room`, `room_state`, `bed`, `bed_state`, `bed_facility`.

Consult order tables: `consultation_request`, `consultation_type`, `request_answer`.

Answers to Lab Order questions now stored in the `request_answer` table.


#### department

**Attributes**

* department_id
* hl7_string
* name
* speciality

#### department_state

**Attributes**

* department_state_id
* department_id
* status
* valid_from
* valid_until
* stored_from
* stored_until

#### room

**Attributes**

* room_id
* department_id
* hl7_string
* name

#### room_state

**Attributes**

* room_state_id
* room_id
* csn
* status
* is_ready
* valid_from
* valid_until
* stored_from
* stored_until


#### bed

**Attributes**

* bed_id
* room_id
* hl7_string

#### bed_state

**Attributes**

* bed_state_id
* bed_id
* csn
* status
* is_bunk
* is_in_census
* is_ready
* pool_bed_count
* valid_from
* valid_until
* stored_from
* stored_until

#### bed_facility

**Attributes**

* bed_facility_id
* bed_state_id
* type

#### request_answer

**Attributes**

* request_answer_id
* stored_from
* valid_from
* answer
* parent_id
* parent_table
* question_id

#### consultation_request

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

#### consultation_type

**Attributes**

* consultation_type_id
* stored_from
* valid_from
* code
* name

### Deprecated tables

#### lab_sample_question

#### lab_sample_question_audit


### Changes/fixes

* Location metadata has been added

* Consult orders have been added

* Fewer ghosts: Hospital Visits and Location Visits won't be created from a message which updates patient details.

---

## Data sources

Consult orders come from live HL7 feed.

### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.2     |
|Emap_interchange       | 2.2     |
|Emap-Core              | 2.2     |
|Inform-DB              | 2.2     |
|Hoover                 | 2.2     |
