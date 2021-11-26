








<h2 id="ConditionType">ConditionType</h2>

Type of condition that a patient can have.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| conditionTypeId | bigint | Unique identifier in EMAP for this **ConditionType** record. |
| dataType | varchar(255) | Problem list or patient infection. |
| internalCode | varchar(255) | Code used within source system for this **ConditionType**. |
| name | varchar(255) | Human readable name for this **ConditionType**. |
| standardisedCode | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardisedVocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |

---



<h2 id="PatientCondition">PatientCondition</h2>

Represents patient conditions that start and can end.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| patientConditionId | bigint | Unique identifier in EMAP for this **PatientCondition** record. |
| conditionTypeId | [ConditionType](#ConditionType) | Identifier for the [ConditionType](#ConditionType) associated with this record. |
| internalId | bigint | Identifier used in source system for this **PatientCondition**. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| addedDateTime | timestamp without timezone | Date and time at which this **PatientCondition** was added to the record. |
| resolutionDateTime | timestamp without timezone | Date and time at which this **PatientCondition** was resolved. |
| onsetDate | date | Date at which the **PatientCondition** started (if known). |
| classification | varchar(255) | Problem List classification (e.g. Temporary). |
| status | varchar(255) | Status of **PatientCondition**. |
| priority | varchar(255) | Problem List priority. |
| comment | varchar(255) | Comments added by clinician. |

---



<h2 id="ConsultationRequest">ConsultationRequest</h2>

Holds information relevant to consultation requests for patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultationRequestId | bigint | Unique identifier in EMAP for this **ConsultationRequest** record. |
| consultationTypeId | [ConsultationType](#ConsultationType) | Identifier for the [ConsultationType](#ConsultationType) associated with this record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| internalId | bigint | Identifier used in source system for this **ConsultationRequest**. |
| closedDueToDischarge | boolean | Predicate determining whether this **ConsultationRequest** was closed on discharge. |
| comments | varchar(255) | Notes added to the **ConsultationRequest** which are not tied to a Question. |
| statusChangeTime | timestamp without timezone | Date and time at which this **ConsultationRequest** was last updated. |
| scheduledDatetime | timestamp without timezone | Date and time at which this **ConsultationRequest** was scheduled. |
| cancelled | boolean | Predicate determining whether this **ConsultationRequest** has been cancelled by a user. |

---



<h2 id="ConsultationType">ConsultationType</h2>

Type of a ConsultationRequest made for a patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| consultationTypeId | bigint | Unique identifier in EMAP for this **ConsultationType** record. |
| code | varchar(255) | Code used in source system for this **ConsultationType**. |
| name | varchar(255) | Human readable name for this **ConsultationType**. |

---



<h2 id="advance_decision">AdvanceDecision</h2>

Holds information relevant to advance decisions taken by patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advanceDecisionId | bigint | Unique identifier in EMAP for this **AdvanceDecision** record. |
| advanceDecisionTypeId | [AdvanceDecisionType](#AdvanceDecisionType) | Identifier for the [AdvanceDecisionType](#AdvanceDecisionType) associated with this record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| internalId | bigint | Identifier used in source system for this **AdvanceDecision**. |
| closedDueToDischarge | boolean | Predicate determining whether this **AdvanceDecision** was closed on discharge. |
| statusChangeDatetime | timestamp without timezone | Date and time at which this **AdvanceDecision** was last updated. |
| requestedDatetime | timestamp without timezone | Date and time at which this **AdvanceDecision** was first recorded. |
| cancelled | boolean | Predicate determining whether this **AdvanceDecision** has been cancelled by a user. |

---



<h2 id="AdvanceDecisionType">AdvanceDecisionType</h2>

Types of AdvancedDecision that can be recorded.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| advanceDecisionTypeId | bigint | Unique identifier in EMAP for this **AdvanceDecisionType** record. |
| name | varchar(255) | Name of the **AdvanceDecisionType**, e.g. DNACPR. |
| careCode | varchar(255) | Code used within source system for **AdvanceDecisionType**, e.g COD4 for DNACPR. |

---



<h2 id="CoreDemographic">CoreDemographic</h2>

A core demographic represents the main demographics stored around patients.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| coreDemographicId | bigint | Unique identifier in EMAP for this **CoreDemographic** record. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| firstname | varchar(255) | First name of the patient. |
| middlename | varchar(255) | Middle name of the patient. |
| lastname | varchar(255) | Last name of the patient. |
| dateOfBirth | date | Date of birth of the patient. |
| dateOfDeath | date | Date of death of the patient. |
| datetimeOfBirth | timestamp without timezone | Date and time of birth of the patient. |
| datetimeOfDeath | timestamp without timezone | Date and time of death of the patient. |
| alive | boolean | Predicate determining whether the patient is alive. |
| homePostcode | varchar(255) | Postcode of the patient's home address. |
| sex | varchar(255) | Sex of the patient. |
| ethnicity | varchar(255) | Ethnicity of the patient. |

---



<h2 id="HospitalVisit">HospitalVisit</h2>

This a single visit to the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| hospitalVisitId | bigint | Unique identifier in EMAP for this **HospitalVisit** record. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| sourceSystem | varchar(255) | The source system from which we learnt about this hospital visit. |
| presentationTime | timestamp without timezone | Date and time at which this **HospitalVisit** was first recorded. |
| admissionTime | timestamp without timezone | Date and time at which this **HospitalVisit** formally began. |
| dischargeTime | timestamp without timezone | Date and time at which this **HospitalVisit** formally ended. |
| patientClass | varchar(255) | The patient class. E.g. Inpatient or Outpaitent. |
| arrivalMethod | varchar(255) | The patient's arrival method at hospital. |
| dischargeDestination | varchar(255) | Where the patient went after their departure. |
| dischargeDisposition | varchar(255) | The patient's disposition on departure. |
| encounter | varchar(255) | The source system identifier of this hospital visit. |
| visitObservations | Missing Type | Visit observations should be deleted if an encounter is deleted. |

---



<h2 id="Mrn">Mrn</h2>

This represents the association of Medical Resource Number (MRN) to an individual patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrnId | bigint | Unique identifier in EMAP for this **Mrn** record. |
| hospitalVisits | Missing Type | None |
| mrn | varchar(255) | The value of the MRN identifier. |
| nhsNumber | varchar(255) | NHS number. |
| sourceSystem | varchar(255) | The system from which this MRN was initially discovered. |
| storedFrom | timestamp without timezone | Date and time at which this **Mrn** was first recorded in EMAP. |

---



<h2 id="MrnToLive">MrnToLive</h2>

This table stores a mapping from every MRN known to the system, to its currently live (in use) MRN.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| mrnToLiveId | bigint | Unique identifier in EMAP for this **MrnToLive** record. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| liveMrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |

---



<h2 id="LabBattery">LabBattery</h2>

This represents all the different batteries of test that can be ordered.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labBatteryId | bigint | Unique identifier in EMAP for this **LabBattery** record. |
| batteryCode | varchar(255) | Code for this battery of tests. |
| batteryName | varchar(255) | Human readable name for this battery of tests. |
| description | varchar(255) | Desription of this battery of tests. |
| labProvider | varchar(255) | Source system of this batteryCode. |

---



<h2 id="LabBatteryElement">LabBatteryElement</h2>

This represents all the different batteries of test that can be ordered.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labBatteryElementId | bigint | Unique identifier in EMAP for this **LabBatteryElement** record. |
| labBatteryId | [LabBattery](#LabBattery) | Identifier for the [LabBattery](#LabBattery) associated with this record. |
| labTestDefinitionId | [LabTestDefinition](#LabTestDefinition) | Identifier for the [LabTestDefinition](#LabTestDefinition) associated with this record. |

---



<h2 id="LabIsolate">LabIsolate</h2>

Isolates identified from culture.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labIsolateId | bigint | Unique identifier in EMAP for this **LabIsolate** record. |
| labResultId | [LabResult](#LabResult) | Identifier for the [LabResult](#LabResult) associated with this record. |
| labInternalId | varchar(255) | Internal Id of the **LabIsolate**. |
| isolateCode | varchar(255) | Lab system's code for the isolate. |
| isolateName | varchar(255) | Name of the isolate. |
| cultureType | varchar(255) | Method of culture. |
| quantity | varchar(255) | Usually CFU range, but can also be categorical. |
| clinicalInformation | varchar(255) | Any clinical information for the isolate. |

---



<h2 id="LabOrder">LabOrder</h2>

A LabOrder contains the details of the request to perform a lab investigation.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labOrderId | bigint | Unique identifier in EMAP for this **LabOrder** record. |
| labSampleId | [LabSample](#LabSample) | Identifier for the [LabSample](#LabSample) associated with this record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| labBatteryId | [LabBattery](#LabBattery) | Identifier for the [LabBattery](#LabBattery) associated with this record. |
| orderDatetime | timestamp without timezone | Date and time at which this **LabOrder** was actioned. |
| requestDatetime | timestamp without timezone | Date and time at which this **LabOrder** was requested. |
| clinicalInformation | varchar(255) | Additional information supplied. |
| internalLabNumber | varchar(255) | Identifier used in source system for this **LabOrder**. |
| sourceSystem | varchar(255) | Name of the source system where this **LabOrder** was created. |

---



<h2 id="LabResult">LabResult</h2>

A LabResult is a single component result of a lab. A single order or sample is likely to produce several results.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labResultId | bigint | Unique identifier in EMAP for this **LabResult** record. |
| labOrderId | [LabOrder](#LabOrder) | Identifier for the [LabOrder](#LabOrder) associated with this record. |
| labTestDefinitionId | [LabTestDefinition](#LabTestDefinition) | Identifier for the [LabTestDefinition](#LabTestDefinition) associated with this record. |
| resultLastModifiedTime | timestamp without timezone | Date and time at which the **LabResult** was last modified. |
| abnormalFlag | varchar(255) | Lab system flag for value outside of normal range. |
| mimeType | varchar(255) | Mime type (or custom type) of the value. |
| valueAsText | varchar(255) | Value as text. |
| valueAsReal | double precision | Value as a number. |
| valueAsBytes | bytea | Value as bytes. |
| resultOperator | varchar(255) | For numeric results, defines the operator used to define the value. |
| rangeHigh | double precision | Upper limit of reference range. |
| rangeLow | double precision | Lower limit of reference range. |
| resultStatus | varchar(255) | Status of the result. |
| units | varchar(255) | Units of the result. |
| comment | varchar(255) | Additional comments. |

---



<h2 id="LabSample">LabSample</h2>

A LabSample details the external lab's view of a sample being analysed and its receipt by the lab system.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labSampleId | bigint | Unique identifier in EMAP for this **LabSample** record. |
| mrnId | [Mrn](#Mrn) | Identifier for the [Mrn](#Mrn) associated with this record. |
| externalLabNumber | varchar(255) | Lab number for the system doing the lab test. |
| Instant | Missing Type | Date and time at which this **LabSample** arrived at the lab. |
| sampleCollectionTime | [Instant](#Instant) | Date and time at which this **LabSample** was take from the patient. |
| specimenType | varchar(255) | Type of specimen. |
| sampleSite | varchar(255) | Site on body the sample was taken from. |
| collectionMethod | varchar(255) | Method of collection. |

---



<h2 id="LabSensitivity">LabSensitivity</h2>

Sensitivities show the affect of specific agents on isolates from cultures.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labSensitivityId | bigint | Unique identifier in EMAP for this **LabSensitivity** record. |
| labIsolateId | [LabIsolate](#LabIsolate) | Identifier for the [LabIsolate](#LabIsolate) associated with this record. |
| agent | varchar(255) | The chemical (often antibiotic) used. |
| sensitivity | varchar(255) | Sensitivity of the microbe to the agent. |
| reportingDatetime | timestamp without timezone | Date and time at which this **LabSensitivity** was reported. |

---



<h2 id="LabTestDefinition">LabTestDefinition</h2>

This represents the definition of a single lab test by a single provider.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| labTestDefinitionId | bigint | Unique identifier in EMAP for this **LabTestDefinition** record. |
| labProvider | varchar(255) | What system this code belongs to. Examples could be WinPath, or Epic. |
| labDepartment | varchar(255) | The department within the lab responsible for the test. |
| testLabCode | varchar(255) | The code for this test as reported by the lab. |
| testStandardCode | varchar(255) | The code for this test in a standardised vocabulary. |
| standardisedVocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |

---



<h2 id="Bed">Bed</h2>

Represents a bed in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bedId | bigint | Unique identifier in EMAP for this **Bed** record. |
| roomId | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| hl7String | varchar(255) | Text name used by HL7 for this **Bed**. |

---



<h2 id="BedFacility">BedFacility</h2>

Represents a facility available at a Bed.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bedFacilityId | bigint | Unique identifier in EMAP for this **BedFacility** record. |
| bedStateId | [BedState](#BedState) | Identifier for the [BedState](#BedState) associated with this record. |
| type | varchar(255) | Type of facility available at bed. |

---



<h2 id="BedState">BedState</h2>

Represents the state of a given Bed.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| bedStateId | bigint | Unique identifier in EMAP for this **BedState** record. |
| bedId | [Bed](#Bed) | Identifier for the [Bed](#Bed) associated with this record. |
| csn | bigint | Indentifier ?? |
| isInCensus | boolean | Predicate determining whether the Bed is in census. |
| isBunk | boolean | Predicate determining whether the Bed is a bunk. |
| status | varchar(255) | Current status of the Bed. |
| poolBedCount | bigint | Pool bed count ?? |

---



<h2 id="Department">Department</h2>

Represents a department in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| departmentId | bigint | Unique identifier in EMAP for this **Department** record. |
| hl7String | varchar(255) | Text name used by HL7 for this **Department**. |
| name | varchar(255) | Name of this **Department**. |
| speciality | varchar(255) | Speciality of this **Department**. |

---



<h2 id="DepartmentState">DepartmentState</h2>

Represents the state of a given Department.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| departmentStateId | bigint | Unique identifier in EMAP for this **DepartmentState** record. |
| departmentId | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| status | varchar(255) | Current status of the Department. |

---



<h2 id="Location">Location</h2>

\breif Known locations within the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| locationId | bigint | Unique identifier in EMAP for this **Location** record. |
| locationString | varchar(255) | Text value of the **Location**. |
| departmentId | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| roomId | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| bedId | [Bed](#Bed) | Identifier for the [Bed](#Bed) associated with this record. |

---



<h2 id="LocationVisit">LocationVisit</h2>

This represents a patient being in a location for an amount of time.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| locationVisitId | bigint | Unique identifier in EMAP for this **LocationVisit** record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| parentLocationVisitId | bigint | Identifier of the parent **LocationVisit**. |
| admissionTime | timestamp without timezone | Date and time at which the patient was admitted to this location. |
| dischargeTime | timestamp without timezone | Date and time at which the patient was discharged from this location. |
| locationId | [Location](#Location) | Identifier of the [Location](#Location) associated with this **LocationVisit**. |
| inferredAdmission | boolean | Predicate determining whether the admission time has been inferred (not set from an A01, A02 or A03). |
| inferredDischarge | boolean | Predicate determining whether discharge time has been inferred (not set from an A01, A02 or A03). |

---



<h2 id="Room">Room</h2>

Represents a room in the hospital.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| roomId | bigint | Unique identifier in EMAP for this **Room** record. |
| departmentId | [Department](#Department) | Identifier for the [Department](#Department) associated with this record. |
| hl7String | varchar(255) | Text name used by HL7 for this **Room**. |
| name | varchar(255) | Name for this **Room**. |

---



<h2 id="RoomState">RoomState</h2>

Represents the state of a given Room.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| roomStateId | bigint | Unique identifier in EMAP for this **RoomState** record. |
| roomId | [Room](#Room) | Identifier for the [Room](#Room) associated with this record. |
| csn | bigint | Indentifier ?? |
| status | varchar(255) | Current status of the Room. |
| isReady | boolean | Predicate determining whether the Room is ready. |

---



<h2 id="Question">Question</h2>

Questions that can be attached to several data types, such as lab samples or consultation requests.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| questionId | bigint | Unique identifier in EMAP for this **Question** record. |
| question | varchar(255) | Text content of the **Question**. |
| storedFrom | timestamp without timezone | Date and time from which this **Question** is stored. |
| validFrom | timestamp without timezone | Date and time from which this **Question** is valid. |

---



<h2 id="RequestAnswer">RequestAnswer</h2>

Answers to questions listed in Question table.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| requestAnswerId | bigint | Unique identifier in EMAP for this **RequestAnswer**Id record. |
| answer | varchar(255) | Text content of the **RequestAnswer**. |
| questionId | [Question](#Question) | Identifier for the [Question](#Question) associated with this record. |
| parentTable | varchar(255) | Parent table that should be included as a part of the join. |
| parentId | bigint | Identifier for the parentTable associated with this record. |

---



<h2 id="VisitObservation">VisitObservation</h2>

An observation recorded about patient.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visitObservationId | bigint | Unique identifier in EMAP for this **VisitObservation** record. |
| visitObservationTypeId | [VisitObservationType](#VisitObservationType) | Identifier for the [VisitObservationType](#VisitObservationType) associated with this record. |
| hospitalVisitId | [HospitalVisit](#HospitalVisit) | Identifier for the [HospitalVisit](#HospitalVisit) associated with this record. |
| observationDatetime | timestamp without timezone | Date and time at which this **VisitObservation** was first made. |
| valueAsText | varchar(255) | Value as text. |
| valueAsReal | double precision | Value as a number. |
| valueAsDate | date | Value as a date. |
| unit | varchar(255) | Units of the **VisitObservation**. |
| comment | varchar(255) | Comments added by clinician. |

---



<h2 id="VisitObservationType">VisitObservationType</h2>

VisitObservationType describes the meaning behind a specific observation.

### **Attributes/Column Headers**

| Name | Type | Description |
|---| --- |---|
| visitObservationTypeId | bigint | Unique identifier in EMAP for this **VisitObservationType**Id record. |
| sourceSystem | varchar(255) | The source system from which we learnt about this **VisitObservationType**. |
| sourceObservationType | varchar(255) | The data type in the source system. |
| idInApplication | varchar(255) | The code used by the source system to identify the observation type. |
| name | varchar(255) | Readable name for the source system observation type. |
| displayName | varchar(255) | Name displayed to users. |
| description | varchar(255) | Description of the data type. |
| standardisedCode | varchar(255) | Mapping code for the observation from the standardised vocabulary system. Not yet implemented. |
| standardisedVocabulary | varchar(255) | Nomenclature or classification system used. Not yet implemented. |
| primaryDataType | varchar(255) | Data type expected to be returned. |
| creationTime | timestamp without timezone | Date and time at which this **VisitObservationType** was created in the source system. |

---
