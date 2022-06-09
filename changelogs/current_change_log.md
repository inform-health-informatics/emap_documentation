# EMAP Release

**Date: __TODO: FIXME__ Changes in this release**

---

### Tables changed

Table           | Attributes added | Attributes removed | Renamed
:-- |:-- |:--
Patient_condition     | added_datetime | added_date_time | ✓
Patient_condition     | resolution_date_time |resolution_datetime | ✓
Consultation_request  | status_change_time |status_change_datetime | ✓
Hospital_visit        | presentation_datetime | presentation_time | ✓
Hospital_visit        | admission_datetime | admission_time | ✓
Hospital_visit        | discharge_datetime | discharge_time | ✓
Lab_sample            | receipt_at_lab_datetime | receipt_at_lab | ✓
Lab_sample            | sample_collection_datetime | sample_collection_time | ✓
Location_visit        | admission_datetime | admission_time | ✓
Location_visit        | discharge_datetime | discharge_time | ✓
Visit_observation_type | creation_datetime | creation_time | ✓


### Changes/fixes

- Modifies column names with a data type that includes a data and a time to have a _datetime suffix


---
<!--
## Data sources



### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.4     |
|Emap_interchange       | 2.4     |
|Emap-Core              | 2.4     |
|Inform-DB              | 2.4     |
|Hoover                 | 2.4     |
>
