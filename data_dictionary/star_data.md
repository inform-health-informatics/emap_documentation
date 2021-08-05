
# Tables in star database

## mrn

The mrn table stores the unique hospital identifier and NHS numer for a patient, recording the system from which the information was derived and the date from which star stored the data.
The columns and their data types are detailed below.

* <a id="mrn_att">mrn_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* mrn
  * varchar (255)
  
  The mrn is the medical record number for a patient.

* nhs_number
  * varchar (255)

  The nhs_number is the unique NHS number for a patient.

* source_system
  * varchar (255)

  The system that produced the message from which this information was retrieved.
  
  Possible values are 'Not in Message', 'EPIC', 'caboodle', 'ABL90 FLEX Plus', 'WinPath', 'CoPath', 'COPATHPLUS', 'BIO-CONNECT' or a blank entry.

* stored_from
  * timestamp with timezone

  The exact time at which this data was recorded in star.

---

## mrn_to_live

This table records which mrn values are currently live.
Note patients may be given more than one mrn.
When this is discovered the records are merged into a single record with one mrn.

* <a id="mrn_to_live_att">mrn_to_live_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* stored_from
  * timestamp with timezone

* valid_from
  * timestamp with timezone

* live_mrn_id
  * varchar (255)

* [mrn_id](#mrn_att)
  * varchar (255)

---

## visit_observation


* <a id="vo_att">visit_observation_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* stored_from
  * timestamp with timezone

* valid_from
  * timestamp with timezone

* comment
  * varchar (255)

* observation_datetime

* unit
  * varchar (255)

* value_as_date

* value_as_real

* value_as_text
  * varchar (255)

* hospital_visit_id
  * varchar (255)

* [visit_observation_type_id](#vot_att)
  * varchar (255)

---

## visit_observation_type

* <a id="vot_att">visit_observation_type_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* stored_from
  * timestamp with timezone

* valid_from
  * timestamp with timezone

* creation_time
  * timestamp without timezone

* description
  * varchar (255)

* display_name
  * varchar (255)

* id_in_application
  * varchar (255)

* name
  * varchar (255)

* primary_data_type
  * varchar (255)

* source_observation_type
  * varchar (255)

* source_system
  * varchar (255)

* standardised_code
  * varchar (255)

* standardised_vocabulary
  * varchar (255)

---
