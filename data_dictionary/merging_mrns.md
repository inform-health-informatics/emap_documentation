# Multiple MRNs

Consider we have been sent the following information.

| | Patient A| | Patient B |
|-|:-:|-|:-:|
| MRN | 54 || 32 |
| NHS no| 427 ||427| 

Corresponding entries in star

mrn table (part)

| mrn_id|mrn|nhs_number
|:-:|:-:|:-:|
|01|54|427|
|02|32|427|

mrn_to_live table (part)

|mrn_to_live_id|live_mrn_id|mrn_id|
|:-:|:-:|:-:|
|96|01|01|
|97|02|02|

Someone realises that Patient A and Patient B are the same person and all the records frm Patent B are mered ino Patient A's reecords.

mrn_to_live table (part)

|mrn_to_live_id|live_mrn_id|mrn_id|
|:-:|:-:|:-:|
|96|01|01|
|97|01|02|