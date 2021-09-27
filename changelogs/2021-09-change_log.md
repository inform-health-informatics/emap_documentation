# EMAP Release

**Date: 2021-09-27 Changes in this release**

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


### Deprecated tables

#### lab_sample_question

#### lab_sample_question_audit


### Changes/fixes

* Location metadata has been added

* Fewer ghosts: Hospital Visits and Location Visits won't be created from a message which updates patient details.

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