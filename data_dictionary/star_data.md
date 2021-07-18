
# Tables in star database

## mrn

* <a id="mrn_att">mrn_id</a>
  * Primary Key
  * identifier for this entry
  * bigint
* mrn
* nhs_number

## mrn_to_live

* mrn_to_live_id
  * Primary Key
  * identifier fo this entry
  * bigint
* stored_from
* valid_from
* live_mrn_id
* [mrn_id](#mrn_att)