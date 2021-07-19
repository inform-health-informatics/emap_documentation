
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
  
  The [mrn](../Glossary.md#M) is the medical record number for a patient.

* nhs_number
  * varchar (255)

  The [nhs_number](../Glossary.md#N) is the unique NHS number for a patient.

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
  * Primary Key
  * identifier fo this entry
  * bigint
* stored_from
* valid_from
* live_mrn_id
* [mrn_id](#mrn_att)

SK Notes sometimes live_mrn_id == mrn_id and sometimes not ?? 