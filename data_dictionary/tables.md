








## ConditionType

Type of condition that a patient can have.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| condition_type_id | bigint | Unique identifier in EMAP for this **ConditionType** record. |
| data_type | varchar(255) | Problem list or patient infection. |
| internal_code | varchar(255) | Code used within source system for this **ConditionType**. |
| name | varchar(255) | Human readable name for this **ConditionType**. |
| standardised_code | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardised_vocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |

---



## ConditionTypeAudit

Audit table of ConditionType.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| condition_type_audit_id | bigint | None |
| condition_type_id | bigint | None |
| data_type | varchar(255) | None |
| internal_code | varchar(255) | None |
| name | varchar(255) | None |
| standardised_code | varchar(255) | None |
| standardised_vocabulary | varchar(255) | None |

---



## PatientCondition

Represents patient conditions that start and can end.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| patient_condition_id | bigint | Unique identifier in EMAP for this **PatientCondition** record. |
| condition_type_id | [ConditionType](#ConditionType) | Identifier for the [ConditionType](#ConditionType) associated with this record. |
| internal_id | bigint | Identifier used in source system for this **PatientCondition**. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| added_date_time | timestamp without timezone | Date and time at which this **PatientCondition** was added to the record. |
| resolution_date_time | timestamp without timezone | Date and time at which this **PatientCondition** was resolved. |
| onset_date | date | Date at which the **PatientCondition** started (if known). |
| classification | varchar(255) | Problem List classification (e.g. Temporary). |
| status | varchar(255) | Status of **PatientCondition**. |
| priority | varchar(255) | Problem List priority. |
| comment | varchar(255) | Comments added by clinician. |

---



## PatientConditionAudit

Audit table of PatientCondition.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| patient_condition_audit_id | bigint | None |
| patient_condition_id | bigint | None |
| condition_type_id | bigint | None |
| internal_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| hospital_visit_id | bigint | None |
| added_datetime | timestamp without timezone | None |
| resolution_datetime | timestamp without timezone | None |
| onset_date | date | None |
| classification | varchar(255) | None |
| status | varchar(255) | None |
| priority | varchar(255) | None |
| comment | varchar(255) | None |

---



## ConsultationRequest

Holds information relevant to consultation requests for patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultation_request_id | bigint | Unique identifier in EMAP for this **ConsultationRequest** record. |
| consultation_type_id | [ConsultationType](#ConsultationType) | Identifier for the [ConsultationType](#ConsultationType) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| internal_id | bigint | Identifier used in source system for this **ConsultationRequest**. |
| closed_due_to_discharge | boolean | Predicate determining whether this **ConsultationRequest** was closed on discharge. |
| comments | varchar(255) | Notes added to the **ConsultationRequest** which are not tied to a Question. |
| status_change_time | timestamp without timezone | Date and time at which this **ConsultationRequest** was last updated. |
| scheduled_datetime | timestamp without timezone | Date and time at which this **ConsultationRequest** was scheduled. |
| cancelled | boolean | Predicate determining whether this **ConsultationRequest** has been cancelled by a user. |

---



## ConsultationRequestAudit

Audit table of ConsultationRequest.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultation_request_audit_id | bigint | None |
| consultation_request_id | bigint | None |
| consultation_type_id | bigint | None |
| hospital_visit_id | bigint | None |
| internal_id | bigint | None |
| closed_due_to_discharge | boolean | None |
| comments | varchar(255) | None |
| status_change_datetime | timestamp without timezone | None |
| scheduled_datetime | timestamp without timezone | None |
| cancelled | boolean | None |

---



## ConsultationType

Type of a ConsultationRequest made for a patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultation_type_id | bigint | Unique identifier in EMAP for this **ConsultationType** record. |
| code | varchar(255) | Code used in source system for this **ConsultationType**. |
| name | varchar(255) | Human readable name for this **ConsultationType**. |

---



## ConsultationTypeAudit

Audit table of ConsultationType.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultation_type_audit_id | bigint | None |
| consultation_type_id | bigint | None |
| code | varchar(255) | None |
| name | varchar(255) | None |

---



## AdvanceDecision

Holds information relevant to advance decisions taken by patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advance_decision_id | bigint | Unique identifier in EMAP for this **AdvanceDecision** record. |
| advance_decision_type_id | [AdvanceDecisionType](#AdvanceDecisionType) | Identifier for the [AdvanceDecisionType](#AdvanceDecisionType) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| internal_id | bigint | Identifier used in source system for this **AdvanceDecision**. |
| closed_due_to_discharge | boolean | Predicate determining whether this **AdvanceDecision** was closed on discharge. |
| status_change_datetime | timestamp without timezone | Date and time at which this **AdvanceDecision** was last updated. |
| requested_datetime | timestamp without timezone | Date and time at which this **AdvanceDecision** was first recorded. |
| cancelled | boolean | Predicate determining whether this **AdvanceDecision** has been cancelled by a user. |

---



## AdvanceDecisionAudit

Audit table of AdvanceDecision.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advance_decision_audit_id | bigint | None |
| advance_decision_id | bigint | None |
| advance_decision_type_id | [uk.ac.ucl.rits.inform.informdb.decisions.AdvanceDecisionType](#uk.ac.ucl.rits.inform.informdb.decisions.AdvanceDecisionType) | None |
| hospital_visit_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| internal_id | bigint | None |
| closed_due_to_discharge | boolean | None |
| status_change_datetime | timestamp without timezone | None |
| requested_datetime | timestamp without timezone | None |
| cancelled | boolean | None |

---



## AdvanceDecisionType

Types of AdvancedDecision that can be recorded.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advance_decision_type_id | bigint | Unique identifier in EMAP for this **AdvanceDecisionType** record. |
| name | varchar(255) | Name of the **AdvanceDecisionType**, e.g. DNACPR. |
| care_code | varchar(255) | Code used within source system for **AdvanceDecisionType**, e.g COD4 for DNACPR. |

---



## CoreDemographic

A core demographic represents the main demographics stored around patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| core_demographic_id | bigint | Unique identifier in EMAP for this **CoreDemographic** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| firstname | varchar(255) | First name of the patient. |
| middlename | varchar(255) | Middle name of the patient. |
| lastname | varchar(255) | Last name of the patient. |
| date_of_birth | date | Date of birth of the patient. |
| date_of_death | date | Date of death of the patient. |
| datetime_of_birth | timestamp without timezone | Date and time of birth of the patient. |
| datetime_of_death | timestamp without timezone | Date and time of death of the patient. |
| alive | boolean | Predicate determining whether the patient is alive. |
| home_postcode | varchar(255) | Postcode of the patient's home address. |
| sex | varchar(255) | Sex of the patient. |
| ethnicity | varchar(255) | Ethnicity of the patient. |

---



## CoreDemographicAudit

Audit table of CoreDemographic.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| core_demographic_audit_id | bigint | None |
| core_demographic_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| firstname | varchar(255) | None |
| middlename | varchar(255) | None |
| lastname | varchar(255) | None |
| date_of_birth | date | None |
| date_of_death | date | None |
| datetime_of_birth | timestamp without timezone | None |
| datetime_of_death | timestamp without timezone | None |
| alive | boolean | None |
| home_postcode | varchar(255) | None |
| sex | varchar(255) | None |
| ethnicity | varchar(255) | None |

---



## HospitalVisit

This a single visit to the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| hospital_visit_id | bigint | Unique identifier in EMAP for this **HospitalVisit** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| source_system | varchar(255) | The source system from which we learnt about this hospital visit. |
| presentation_time | timestamp without timezone | Date and time at which this **HospitalVisit** was first recorded. |
| admission_time | timestamp without timezone | Date and time at which this **HospitalVisit** formally began. |
| discharge_time | timestamp without timezone | Date and time at which this **HospitalVisit** formally ended. |
| patient_class | varchar(255) | The patient class. E.g. Inpatient or Outpaitent. |
| arrival_method | varchar(255) | The patient's arrival method at hospital. |
| discharge_destination | varchar(255) | Where the patient went after their departure. |
| discharge_disposition | varchar(255) | The patient's disposition on departure. |
| encounter | varchar(255) | The source system identifier of this hospital visit. |
| visit_observations | Missing Type | Visit observations should be deleted if an encounter is deleted. |

---



## HospitalVisitAudit

Audit table of HospitalVisit.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| hospital_visit_audit_id | bigint | None |
| hospital_visit_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| source_system | varchar(255) | None |
| presentation_datetime | timestamp without timezone | None |
| admission_datetime | timestamp without timezone | None |
| discharge_datetime | timestamp without timezone | None |
| patient_class | varchar(255) | None |
| arrival_method | varchar(255) | None |
| discharge_destination | varchar(255) | None |
| discharge_disposition | varchar(255) | None |
| encounter | varchar(255) | None |

---



## Mrn

This represents the association of Medical Resource Number (MRN) to an individual patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrn_id | bigint | Unique identifier in EMAP for this **Mrn** record. |
| hospital_visits | Missing Type | None |
| mrn | varchar(255) | The value of the MRN identifier. |
| nhs_number | varchar(255) | NHS number. |
| source_system | varchar(255) | The system from which this MRN was initially discovered. |
| stored_from | timestamp without timezone | Date and time at which this **Mrn** was first recorded in EMAP. |

---



## MrnToLive

This table stores a mapping from every MRN known to the system, to its currently live (in use) MRN.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrn_to_live_id | bigint | Unique identifier in EMAP for this **MrnToLive** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| live_mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |

---



## MrnToLiveAudit

Audit table of MrnToLive.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrn_to_live_audit_id | bigint | None |
| mrn_to_live_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| live_mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |

---



## ClimbSequenceAudit

Audit table of ClimbSequence.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| climb_sequence_audit_id | bigint | None |
| climb_sequence_id | bigint | None |
| lab_sample_id | bigint | None |
| fasta_header | varchar(255) | None |
| sequence | varchar(255) | None |
| cog_id | varchar(255) | None |
| phe_id | varchar(255) | None |
| collection_date | date | None |

---



## LabBattery

This represents all the different batteries of test that can be ordered.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_battery_id | bigint | Unique identifier in EMAP for this **LabBattery** record. |
| battery_code | varchar(255) | Code for this battery of tests. |
| battery_name | varchar(255) | Human readable name for this battery of tests. |
| description | varchar(255) | Desription of this battery of tests. |
| lab_provider | varchar(255) | Source system of this batteryCode. |

---



## LabBatteryAudit

Audit table of LabBattery.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_battery_audit_id | bigint | None |
| lab_battery_id | bigint | None |
| battery_code | varchar(255) | None |
| battery_name | varchar(255) | None |
| description | varchar(255) | None |
| lab_provider | varchar(255) | None |

---



## LabBatteryElement

This represents all the different batteries of test that can be ordered.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_battery_element_id | bigint | Unique identifier in EMAP for this **LabBatteryElement** record. |
| lab_battery_id | [LabBattery](#LabBattery) | Identifier for the [LabBattery](#LabBattery) associated with this record. |
| lab_test_definition_id | [LabTestDefinition](#LabTestDefinition) | Identifier for the [LabTestDefinition](#LabTestDefinition) associated with this record. |

---



## LabBatteryElementAudit

Audit table of LabBatteryElement.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_battery_element_audit_id | bigint | None |
| lab_battery_element_id | bigint | None |
| lab_battery_id | bigint | None |
| lab_test_definition_id | bigint | None |

---



## LabIsolate

Isolates identified from culture.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_isolate_id | bigint | Unique identifier in EMAP for this **LabIsolate** record. |
| lab_result_id | [LabResult](#LabResult) | Identifier for the [LabResult](#LabResult) associated with this record. |
| lab_internal_id | varchar(255) | Internal Id of the **LabIsolate**. |
| isolate_code | varchar(255) | Lab system's code for the isolate. |
| isolate_name | varchar(255) | Name of the isolate. |
| culture_type | varchar(255) | Method of culture. |
| quantity | varchar(255) | Usually CFU range, but can also be categorical. |
| clinical_information | varchar(255) | Any clinical information for the isolate. |

---



## LabIsolateAudit

Audit table of LabIsolate.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_isolate_audit_id | bigint | None |
| lab_isolate_id | bigint | None |
| lab_result_id | bigint | None |
| lab_internal_id | varchar(255) | None |
| isolate_code | varchar(255) | None |
| isolate_name | varchar(255) | None |
| culture_type | varchar(255) | None |
| quantity | varchar(255) | None |
| clinical_information | varchar(255) | None |

---



## LabOrder

A LabOrder contains the details of the request to perform a lab investigation.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_order_id | bigint | Unique identifier in EMAP for this **LabOrder** record. |
| lab_sample_id | [LabSample](#LabSample) | Identifier for the [LabSample](#LabSample) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| lab_battery_id | [LabBattery](#LabBattery) | Identifier for the [LabBattery](#LabBattery) associated with this record. |
| order_datetime | timestamp without timezone | Date and time at which this **LabOrder** was actioned. |
| request_datetime | timestamp without timezone | Date and time at which this **LabOrder** was requested. |
| clinical_information | varchar(255) | Additional information supplied. |
| internal_lab_number | varchar(255) | Identifier used in source system for this **LabOrder**. |
| source_system | varchar(255) | Name of the source system where this **LabOrder** was created. |

---



## LabOrderAudit

Audit table of LabOrder.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_order_audit_id | bigint | None |
| lab_order_id | bigint | None |
| lab_sample_id | bigint | None |
| hospital_visit_id | bigint | None |
| lab_battery_id | bigint | None |
| order_datetime | timestamp without timezone | None |
| request_datetime | timestamp without timezone | None |
| clinical_information | varchar(255) | None |
| internal_lab_number | varchar(255) | None |
| source_system | varchar(255) | None |

---



## LabResult

A LabResult is a single component result of a lab. A single order or sample is likely to produce several results.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_result_id | bigint | Unique identifier in EMAP for this **LabResult** record. |
| lab_order_id | [LabOrder](#LabOrder) | Identifier for the [LabOrder](#LabOrder) associated with this record. |
| lab_test_definition_id | [LabTestDefinition](#LabTestDefinition) | Identifier for the [LabTestDefinition](#LabTestDefinition) associated with this record. |
| result_last_modified_time | timestamp without timezone | Date and time at which the **LabResult** was last modified. |
| abnormal_flag | varchar(255) | Lab system flag for value outside of normal range. |
| mime_type | varchar(255) | Mime type (or custom type) of the value. |
| value_as_text | varchar(255) | Value as text. |
| value_as_real | double precision | Value as a number. |
| value_as_bytes | bytea | Value as bytes. |
| result_operator | varchar(255) | For numeric results, defines the operator used to define the value. |
| range_high | double precision | Upper limit of reference range. |
| range_low | double precision | Lower limit of reference range. |
| result_status | varchar(255) | Status of the result. |
| units | varchar(255) | Units of the result. |
| comment | varchar(255) | Additional comments. |

---



## LabResultAudit

Audit table of LabResult.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_result_audit_id | bigint | None |
| lab_result_id | bigint | None |
| lab_order_id | bigint | None |
| lab_test_definition_id | bigint | None |
| result_last_modified_datetime | timestamp without timezone | None |
| abnormal_flag | varchar(255) | None |
| mime_type | varchar(255) | None |
| value_as_text | varchar(255) | None |
| value_as_real | double precision | None |
| value_as_bytes | bytea | None |
| result_operator | varchar(255) | None |
| range_high | double precision | None |
| range_low | double precision | None |
| result_status | varchar(255) | None |
| units | varchar(255) | None |
| comment | varchar(255) | None |

---



## LabSample

A LabSample details the external lab's view of a sample being analysed and its receipt by the lab system.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_sample_id | bigint | Unique identifier in EMAP for this **LabSample** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| external_lab_number | varchar(255) | Lab number for the system doing the lab test. |
| receipt_at_lab | timestamp without timezone | Date and time at which this **LabSample** arrived at the lab. |
| sample_collection_time | timestamp without timezone | Date and time at which this **LabSample** was take from the patient. |
| specimen_type | varchar(255) | Type of specimen. |
| sample_site | varchar(255) | Site on body the sample was taken from. |
| collection_method | varchar(255) | Method of collection. |

---



## LabSampleAudit

Audit table of LabSample.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_sample_audit_id | bigint | None |
| lab_sample_id | bigint | None |
| mrn_id | [uk.ac.ucl.rits.inform.informdb.identity.Mrn](#uk.ac.ucl.rits.inform.informdb.identity.Mrn) | None |
| external_lab_number | varchar(255) | None |
| receipt_at_lab_datetime | timestamp without timezone | None |
| sample_collection_datetime | timestamp without timezone | None |
| specimen_type | varchar(255) | None |
| sample_site | varchar(255) | None |
| collection_method | varchar(255) | None |

---



## LabSensitivity

Sensitivities show the affect of specific agents on isolates from cultures.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_sensitivity_id | bigint | Unique identifier in EMAP for this **LabSensitivity** record. |
| lab_isolate_id | [LabIsolate](#LabIsolate) | Identifier for the [LabIsolate](#LabIsolate) associated with this record. |
| agent | varchar(255) | The chemical (often antibiotic) used. |
| sensitivity | varchar(255) | Sensitivity of the microbe to the agent. |
| reporting_datetime | timestamp without timezone | Date and time at which this **LabSensitivity** was reported. |

---



## LabSensitivityAudit

Audit table of LabSensitivity.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_sensitivity_audit_id | bigint | None |
| lab_sensitivity_id | bigint | None |
| lab_isolate_id | bigint | None |
| agent | varchar(255) | None |
| sensitivity | varchar(255) | None |
| reporting_datetime | timestamp without timezone | None |

---



## Bed

Represents a bed in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bed_id | bigint | Unique identifier in EMAP for this **Bed** record. |
| room_id | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| hl7_string | varchar(255) | Text name used by HL7 for this **Bed**. |

---



## BedFacility

Represents a facility available at a Bed.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bed_facility_id | bigint | Unique identifier in EMAP for this **BedFacility** record. |
| bed_state_id | [BedState](#BedState) | Identifier for the [BedState](#BedState) associated with this record. |
| type | varchar(255) | Type of facility available at bed. |

---



## BedState

Represents the state of a given Bed.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bed_state_id | bigint | Unique identifier in EMAP for this **BedState** record. |
| bed_id | [Bed](#Bed) | Identifier for the [Bed](#Bed) associated with this record. |
| csn | bigint | Indentifier ?? |
| is_in_census | boolean | Predicate determining whether the Bed is in census. |
| is_bunk | boolean | Predicate determining whether the Bed is a bunk. |
| status | varchar(255) | Current status of the Bed. |
| pool_bed_count | bigint | Pool bed count ?? |

---



## Department

Represents a department in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| department_id | bigint | Unique identifier in EMAP for this **Department** record. |
| hl7_string | varchar(255) | Text name used by HL7 for this **Department**. |
| name | varchar(255) | Name of this **Department**. |
| speciality | varchar(255) | Speciality of this **Department**. |

---



## DepartmentState

Represents the state of a given Department.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| department_state_id | bigint | Unique identifier in EMAP for this **DepartmentState** record. |
| department_id | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| status | varchar(255) | Current status of the Department. |

---



## Location

\breif Known locations within the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| location_id | bigint | Unique identifier in EMAP for this **Location** record. |
| location_string | varchar(255) | Text value of the **Location**. |
| department_id | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| room_id | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| bed_id | [Bed](#Bed) | Identifier for the [Bed](#Bed) associated with this record. |

---



## LocationVisit

This represents a patient being in a location for an amount of time.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| location_visit_id | bigint | Unique identifier in EMAP for this **LocationVisit** record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| parent_location_visit_id | bigint | Identifier of the parent **LocationVisit**. |
| admission_time | timestamp without timezone | Date and time at which the patient was admitted to this location. |
| discharge_time | timestamp without timezone | Date and time at which the patient was discharged from this location. |
| location_id | [Location](#Location) | Identifier of the [Location](#Location) associated with this **LocationVisit**. |
| inferred_admission | boolean | Predicate determining whether the admission time has been inferred (not set from an A01, A02 or A03). |
| inferred_discharge | boolean | Predicate determining whether discharge time has been inferred (not set from an A01, A02 or A03). |

---



## LocationVisitAudit

Audit table of LocationVisit.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| location_visit_audit_id | bigint | None |
| location_visit_id | bigint | None |
| hospital_visit_id | bigint | None |
| parent_location_visit_id | bigint | None |
| admission_datetime | timestamp without timezone | None |
| discharge_datetime | timestamp without timezone | None |
| location_id | [uk.ac.ucl.rits.inform.informdb.movement.Location](#uk.ac.ucl.rits.inform.informdb.movement.Location) | None |
| inferred_admission | boolean | None |
| inferred_discharge | boolean | None |

---



## Room

Represents a room in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| room_id | bigint | Unique identifier in EMAP for this **Room** record. |
| department_id | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| hl7_string | varchar(255) | Text name used by HL7 for this **Room**. |
| name | varchar(255) | Name for this **Room**. |

---



## RoomState

Represents the state of a given Room.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| room_state_id | bigint | Unique identifier in EMAP for this **RoomState** record. |
| room_id | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| csn | bigint | Indentifier ?? |
| status | varchar(255) | Current status of the Room. |
| is_ready | boolean | Predicate determining whether the Room is ready. |

---



## Question

Questions that can be attached to several data types, such as lab samples or consultation requests.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| question_id | bigint | Unique identifier in EMAP for this **Question** record. |
| question | varchar(255) | Text content of the **Question**. |
| stored_from | timestamp without timezone | Date and time from which this **Question** is stored. |
| valid_from | timestamp without timezone | Date and time from which this **Question** is valid. |

---



## RequestAnswer

Answers to questions listed in Question table.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| request_answer_id | bigint | Unique identifier in EMAP for this **RequestAnswer**Id record. |
| answer | varchar(255) | Text content of the **RequestAnswer**. |
| question_id | [Question](#Question) | Identifier for the [Question](#Question) associated with this record. |
| parent_table | varchar(255) | Parent table that should be included as a part of the join. |
| parent_id | bigint | Identifier for the parentTable associated with this record. |

---



## RequestAnswerAudit

Audit table of RequestAnswer.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| request_answer_audit_id | bigint | None |
| request_answer_id | bigint | None |
| answer | varchar(255) | None |
| question_id | [uk.ac.ucl.rits.inform.informdb.questions.Question](#uk.ac.ucl.rits.inform.informdb.questions.Question) | None |
| parent_table | varchar(255) | None |
| parent_id | bigint | None |

---



## VisitObservation

An observation recorded about patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visit_observation_id | bigint | Unique identifier in EMAP for this **VisitObservation** record. |
| visit_observation_type_id | [VisitObservationType](#VisitObservationType) | Identifier for the [VisitObservationType](#VisitObservationType) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| observation_datetime | timestamp without timezone | Date and time at which this **VisitObservation** was first made. |
| value_as_text | varchar(255) | Value as text. |
| value_as_real | double precision | Value as a number. |
| value_as_date | date | Value as a date. |
| unit | varchar(255) | Units of the **VisitObservation**. |
| comment | varchar(255) | Comments added by clinician. |
| source_system | varchar(255) | The hospital system that emap received the data from (caboodle or EPIC). |

---



## VisitObservationAudit

Audit table of VisitObservation.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visit_observation_audit_id | bigint | None |
| visit_observation_id | bigint | None |
| visit_observation_type_id | bigint | None |
| hospital_visit_id | bigint | None |
| observation_datetime | timestamp without timezone | None |
| value_as_text | varchar(255) | None |
| value_as_real | double precision | None |
| value_as_date | date | None |
| unit | varchar(255) | None |
| comment | varchar(255) | None |
| source_system | varchar(255) | None |

---



## VisitObservationType

VisitObservationType describes the meaning behind a specific observation.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visit_observation_type_id | bigint | Unique identifier in EMAP for this **VisitObservationType**Id record. |
| interface_id | varchar(255) | The ID used in the HL7 messages for referring to this visit observation type. |
| source_observation_type | varchar(255) | The data type in the source system. |
| id_in_application | varchar(255) | The code used by the source system to identify the observation type. |
| name | varchar(255) | Readable name for the source system observation type. |
| display_name | varchar(255) | Name displayed to users. |
| description | varchar(255) | Description of the data type. |
| standardised_code | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardised_vocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |
| primary_data_type | varchar(255) | Data type expected to be returned. |
| creation_time | timestamp without timezone | Date and time at which this **VisitObservationType** was created in the source system. |

---



## VisitObservationTypeAudit

Audit table of VisitObservationType.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visit_observation_type_audit_id | bigint | None |
| visit_observation_type_id | bigint | None |
| interface_id | varchar(255) | None |
| source_observation_type | varchar(255) | None |
| id_in_application | varchar(255) | None |
| name | varchar(255) | None |
| display_name | varchar(255) | None |
| description | varchar(255) | None |
| standardised_code | varchar(255) | None |
| standardised_vocabulary | varchar(255) | None |
| primary_data_type | varchar(255) | None |
| creation_datetime | timestamp without timezone | None |

---
