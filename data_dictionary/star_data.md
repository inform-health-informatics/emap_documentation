
# Tables in star database

## mrn

* <a id="mrn_att">mrn_id</a>
  * bigint
  * Primary Key
  
  The identifier for this table.

* mrn
  * varchar
  
  The [mrn](../Glossary.md#M) is the medical record number for a patient.

* nhs_number
  * varchar

  The [nhs_number](../Glossary.md#N) is the unique NHS number for a patient.

* source_system
  * varchar

  The system that produced the message from which this information was retrieved.
  Possible values are 'EPIC', 'Caboodle'

* stored_from
  * timestamp with timezone

The exact time at which this data was recorded in star.

---

## mrn_to_live

* <a id="mrn_to_live_att">mrn_to_live_id</a>
  * Primary Key
  * identifier fo this entry
  * bigint
* stored_from
* valid_from
* live_mrn_id
* [mrn_id](#mrn_att)