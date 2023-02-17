## AllergenReaction

Reactions to allergens that a patient can have so that it can be recognised by clinical staff.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| allergen_reaction_id | bigint | Unique identifier in EMAP for this **AllergenReaction** record. |
| patient_condition_id | [PatientCondition](#PatientCondition) | Identifier for the [PatientCondition](#PatientCondition) associated with this record. |
| name | varchar(255) | Human readable name for this **AllergenReaction**. |

---

## ConditionType

Type of condition that a patient can have.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| condition_type_id | bigint | Unique identifier in EMAP for this **ConditionType** record. |
| data_type | varchar(255) | Problem list, patient infection or allergy. |
| internal_code | varchar(255) | Code used within source system for this **ConditionType**. |
| name | varchar(255) | Human readable name for this **ConditionType**. |
| sub_type | varchar(255) | Subtype of the condition e.g. an allergy to food. Only populated in the context of allergies. |
| standardised_code | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardised_vocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |

---

## ConditionVisits

Linker table between the PatientCondition and HospitalVisit tables to efficiently model the many-many relationship
between the two.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| condition_visits_id | bigint | Unique identifier in EMAP for this condition visit record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| patient_condition_id | [PatientCondition](#PatientCondition) | Identifier for the [PatientCondition](#PatientCondition) associated with this record. |

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
| added_datetime | timestamp without timezone | Date and time at which this **
PatientCondition** was added to the record. |
| added_date | date | Date at which this **PatientCondition** was added to the record. |
| resolution_datetime | timestamp without timezone | Date and time at which this **PatientCondition** was resolved. |
| resolution_date | date | Date at which this **PatientCondition** was resolved. |
| onset_date | date | Date at which the **PatientCondition** started (if known). |
| classification | varchar(255) | Problem List classification (e.g. Temporary). |
| status | varchar(255) | Status of **PatientCondition**. |
| priority | varchar(255) | condition priority. |
| is_deleted | boolean | Is this condition deleted. |
| comment | varchar(255) | Comments added by clinician. |
| severity | varchar(255) | Description of how severe this condition is. |

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
| closed_due_to_discharge | boolean | Predicate determining whether this **
ConsultationRequest** was closed on discharge. |
| comments | varchar(255) | Notes added to the **ConsultationRequest** which are not tied to a Question. |
| status_change_datetime | timestamp without timezone | Date and time at which this **
ConsultationRequest** was last updated. |
| scheduled_datetime | timestamp without timezone | Date and time at which this **ConsultationRequest** was scheduled. |
| cancelled | boolean | Predicate determining whether this **ConsultationRequest** has been cancelled by a user. |

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

## AdvanceDecision

Holds information relevant to advance decisions taken by patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advance_decision_id | bigint | Unique identifier in EMAP for this **AdvanceDecision** record. |
| advance_decision_type_id | [AdvanceDecisionType](#AdvanceDecisionType) | Identifier for the [AdvanceDecisionType](#AdvanceDecisionType) associated with this record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| internal_id | bigint | Identifier used in source system for this **AdvanceDecision**. |
| closed_due_to_discharge | boolean | Predicate determining whether this **AdvanceDecision** was closed on discharge. |
| status_change_datetime | timestamp without timezone | Date and time at which this **
AdvanceDecision** was last updated. |
| requested_datetime | timestamp without timezone | Date and time at which this **
AdvanceDecision** was first recorded. |
| cancelled | boolean | Predicate determining whether this **AdvanceDecision** has been cancelled by a user. |

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

## HospitalVisit

This a single visit to the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| hospital_visit_id | bigint | Unique identifier in EMAP for this **HospitalVisit** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| source_system | varchar(255) | The source system from which we learnt about this hospital visit. |
| presentation_datetime | timestamp without timezone | Date and time at which this **
HospitalVisit** was first recorded. |
| admission_datetime | timestamp without timezone | Date and time at which this **HospitalVisit** formally began. |
| discharge_datetime | timestamp without timezone | Date and time at which this **HospitalVisit** formally ended. |
| patient_class | varchar(255) | The patient class. E.g. Inpatient or Outpaitent. |
| arrival_method | varchar(255) | The patient's arrival method at hospital. |
| discharge_destination | varchar(255) | Where the patient went after their departure. |
| discharge_disposition | varchar(255) | The patient's disposition on departure. |
| encounter | varchar(255) | The source system identifier of this hospital visit. |
| visit_observations | Missing Type | Visit observations should be deleted if an encounter is deleted. |

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
| research_opt_out | boolean | None |
| source_system | varchar(255) | The system from which this MRN was initially discovered. |
| stored_from | timestamp without timezone | Date and time at which this **Mrn** was first recorded in EMAP. |

---

## MrnToLive

This table stores a mapping from every MRN known to the system, to its currently live (in use) MRN.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrn_to_live_id | bigint | Unique identifier in EMAP for this **MrnToLive** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record, can be merged into another |
| live_mrn_id | [Mrn](#Mrn) | Identifier for the live [Mrn](#Mrn) that should be used (e.g. surviving |

---

## LabBattery

This represents all the different batteries of test that can be ordered.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_battery_id | bigint | Unique identifier in EMAP for this **LabBattery** record. |
| battery_code | varchar(255) | Code for this battery of tests. |
| battery_name | varchar(255) | Human readable name for this battery of tests. |
| lab_provider | varchar(255) | Source system of this batteryCode. |

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

## LabResult

A LabResult is a single component result of a lab. A single order or sample is likely to produce several results.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_result_id | bigint | Unique identifier in EMAP for this **LabResult** record. |
| lab_order_id | [LabOrder](#LabOrder) | Identifier for the [LabOrder](#LabOrder) associated with this record. |
| lab_test_definition_id | [LabTestDefinition](#LabTestDefinition) | Identifier for the [LabTestDefinition](#LabTestDefinition) associated with this record. |
| result_last_modified_datetime | timestamp without timezone | Date and time at which the **
LabResult** was last modified. |
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

## LabSample

A LabSample details the external lab's view of a sample being analysed and its receipt by the lab system.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_sample_id | bigint | Unique identifier in EMAP for this **LabSample** record. |
| mrn_id | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| external_lab_number | varchar(255) | Lab number for the system doing the lab test. |
| receipt_at_lab_datetime | timestamp without timezone | Date and time at which this **LabSample** arrived at the lab. |
| sample_collection_datetime | timestamp without timezone | Date and time at which this **
LabSample** was take from the patient. |
| specimen_type | varchar(255) | Type of specimen. |
| sample_site | varchar(255) | Site on body the sample was taken from. |
| collection_method | varchar(255) | Method of collection. |

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

## LabTestDefinition

This represents the definition of a single lab test by a single provider.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| lab_test_definition_id | bigint | Unique identifier in EMAP for this **LabTestDefinition** record. |
| lab_provider | varchar(255) | What system this code belongs to. Examples could be WinPath, or Epic. |
| lab_department | varchar(255) | The department within the lab responsible for the test. |
| test_lab_code | varchar(255) | The code for this test as reported by the lab. |
| test_standard_code | varchar(255) | The code for this test in a standardised vocabulary. |
| standardised_vocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |
| name | varchar(255) | Human readable name of the lab test. |

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
| admission_datetime | timestamp without timezone | Date and time at which the patient was admitted to this location. |
| discharge_datetime | timestamp without timezone | Date and time at which the patient was discharged from this location. |
| location_id | [Location](#Location) | Identifier of the [Location](#Location) associated with this **
LocationVisit**. |
| inferred_admission | boolean | Predicate determining whether the admission time has been inferred (not set from an A01, A02 or A03). |
| inferred_discharge | boolean | Predicate determining whether discharge time has been inferred (not set from an A01, A02 or A03). |

---

## PlannedMovement

Tracks the final history for each planned movement within the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| planned_movement_id | bigint | Unique identifier in EMAP for this PlannedMovement record. |
| hospital_visit_id | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| location_id | [Location](#Location) | Planned [Location](#Location) to move to, may be null. |
| event_type | varchar(255) | The type of planned movement event (ADMIT, TRANSFER, DISCHARGE). |
| event_datetime | timestamp without timezone | The date and time that the planned movement event was made. |
| cancelled | boolean | Has the planned movement been cancelled (either by a user or because a different movement has occurred). |
| cancelled_datetime | timestamp without timezone | The date and time that the planned movement was cancelled. |

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
| is_real_time | boolean | Does this observation type update in real time? |
| has_visit_observation | boolean | Does this observation type has an associated row in vist_observation? |
| standardised_code | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardised_vocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |
| primary_data_type | varchar(255) | Data type expected to be returned. |
| creation_datetime | timestamp without timezone | Date and time at which this **
VisitObservationType** was created in the source system. |

