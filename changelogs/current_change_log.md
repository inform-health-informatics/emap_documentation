# EMAP Release

**Date: __TODO: FIXME__ Changes in this release**

---

### Tables changed

Table           | Attributes added | Attributes removed | Renamed
:-- |:-- |:--
PatientCondition | addedDatetime | addedDateTime | ✓
PatientCondition | resolutionDateTime |resolutionDatetime | ✓
ConsultationRequest | statusChangeTime |statusChangeDatetime | ✓
HospitalVisit | presentationDatetime | presentationTime | ✓
HospitalVisit | admissionDatetime | admissionTime | ✓
HospitalVisit | dischargeDatetime | dischargeTime | ✓
LabSample | receiptAtLabDatetime | receiptAtLab | ✓
LabSample | sampleCollectionDatetime | sampleCollectionTime | ✓
LocationVisit | admissionDatetime | admissionTime | ✓
LocationVisit | dischargeDatetime | dischargeTime | ✓
VisitObservationType | creationDatetime | creationTime | ✓


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
