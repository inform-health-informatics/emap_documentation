
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
  
  Example possible values are
  'Not in Message',
  'EPIC',
  'caboodle',
  'ABL90 FLEX Plus',
  'WinPath',
  'CoPath',
  'COPATHPLUS',
  'BIO-CONNECT'
  or a blank entry.

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

  The exact time at which this data was recorded in star.

* valid_from
  * timestamp with timezone

  The exact time at which the message recording this observation was sent.

* live_mrn_id
  * varchar (255)

  Orignal MRN from data source.

* [mrn_id](#mrn_att)
  * varchar (255)
  * Foreign Key

  Identifier for this live_mrn_id in mrn table.

---

## visit_observation

* <a id="vo_att">visit_observation_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* stored_from
  * timestamp with timezone

  The exact time at which this data was recorded in star.

* valid_from
  * timestamp with timezone

  The exact time at which the message recording this observation was sent.

* comment
  * varchar (255)
  
  Text recording any comment that was noted with the observation.

* observation_datetime

  The exact time at which this observation was recorded.

* unit
  * varchar (255)

  The units associated with a numerical value for an observation.

* value_as_date
  * date

  Value of the observation where the observation is recorded as a date.

* value_as_real
  * double precision

  Value of the observation where the observaion is recorded as a numerical value.

* value_as_text
  * text

  Value of observation where the observaion is recorded as a text string.

* hospital_visit_id - link in progress
  * varchar (255)
  * Foreign Key

  Identifier of the hospital visit assocated with ths observation.

* [visit_observation_type_id](#vot_att)
  * varchar (255)
  * Foreign Key

  Identifier of the visit_observation_type for this visit_observation.

---

## visit_observation_type

* <a id="vot_att">visit_observation_type_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* stored_from
  * timestamp with timezone

  The exact time at which this data was recorded in star.

* valid_from
  * timestamp with timezone

  The exact time at which the message recording this observation was sent.

* creation_time
  * timestamp without timezone

   The exact time at which this visit_observation_type was created in a source system.

* description
  * varchar (255)

  A description of the observation type. It should be noted that in some cases this field has been used for comments about the observation type.

* display_name
  * varchar (255)

  A short humanly readable name for the observation type.

* id_in_application
  * varchar (255)

  The identifier used by the application retrun an on obsevation type for this particular instance of a type.
  For example, caboodle uses id = 10 for a pulse oxygen observation type.

* name
  * varchar (255)

  A more medically focussed name for the observation type.
  For example, name = 'R OB PIH VISUAL DISTURBANCE' corresponds to display_name = 'Visual Disturbance'.

* primary_data_type
  * varchar (255)

  The type of the data that this observation type records.

  As of August 2021 possible values are:
  'Dosing Parameter',
  'MAR Action',
  'String Type',
  'Height',
  'Blood Pressure',
  'Networked',
  'Custom List',
  'Line/Drain/Airway Link',
  'Dose',
  'Category Type',
  'Patient Height',
  '*Unspecified',
  'Rate',
  'Time',
  'Date',
  'Numeric Type',
  'Concentration',
  'Patient Weight',
  'Weight',
  'Temperature',
  'Image'

* source_observation_type
  * varchar (255)

    The type of observation that has been made for a visit. Currently this is just flowsheets but allows use with other observation types. 

  Possible values are:
  'flowsheet'

* source_system
  * varchar (255)

  The system from which the record was derived.

  Possible values are:
  'EPIC',
  'caboodle'

* standardised_code
  * varchar (255)

  Not yet populated. We hope in future to link observation types to stand onotolgies.

* standardised_vocabulary
  * varchar (255)

  Not yet populated. We hope in future to link observation types to stand onotolgies.

---
