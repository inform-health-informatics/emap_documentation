# EMAP Release

**Date: __TODO: FIXME__ Changes in this release**

---

### Tables changed

Table           | Attributes added | Attributes removed | Renamed
:-- |:-- |:--
patient_condition     | added_datetime | added_date_time | ✓
patient_condition     | resolution_date_time |resolution_datetime | ✓
consultation_request  | status_change_time |status_change_datetime | ✓
hospital_visit        | presentation_datetime | presentation_time | ✓
hospital_visit        | admission_datetime | admission_time | ✓
hospital_visit        | discharge_datetime | discharge_time | ✓
lab_test_definition   | name | | 
lab_sample            | receipt_at_lab_datetime | receipt_at_lab | ✓
lab_sample            | sample_collection_datetime | sample_collection_time | ✓
location_visit        | admission_datetime | admission_time | ✓
location_visit        | discharge_datetime | discharge_time | ✓
visit_observation_type | creation_datetime | creation_time | ✓


### Changes/fixes

- Modifies column names with a data type that includes a data and a time to have a _datetime suffix
- Lab test definitions and batteries now have human readable names

---
<!--
## Data sources



### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.5     |
|Emap_interchange       | 2.5     |
|Emap-Core              | 2.5     |
|Inform-DB              | 2.5     |
|Hoover                 | 2.5     |
>
