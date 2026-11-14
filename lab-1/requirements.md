# Lab 1: Requirements Table

**Problem Statement #13:** Patient Health Record Consent Management System (Healthcare & Telemedicine)

**Name:** Mohammed Tahir Siddique | **SRN:** PES2UG24AM092

## Functional Requirements

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|----|------|-------------|----------|---------------------|-----------|
| FR-001 | Functional | The system shall allow a patient to grant a time-bounded access permission (e.g., 24 hours) for specific selected records to a verified doctor of a registered clinic. | High | **Pass:** A consent is created with the selected records, recipient and expiry timestamp, and clinic access is automatically revoked at the expiry timestamp. **Fail:** The clinic accesses records outside the selected scope, or after the consent has expired. | Granular, time-bound consent is the core purpose of the system. It limits exposure of medical data to the minimum that is needed, for only as long as it is needed. |
| FR-002 | Functional | The system shall allow a patient to revoke any active consent at any time before its expiry. | High | **Pass:** After revocation the consent status changes to "Revoked" and the next access attempt by the clinic is denied. **Fail:** Records are released to the clinic after the patient has revoked the consent. | The patient must stay in control of their data. A consent given by mistake, or no longer needed, should be withdrawable immediately. |
| FR-003 | Functional | The system shall allow a clinic administrator to submit an access request that names the patient, the verified doctor, the record categories, the purpose and the duration, and shall allow the patient to approve or reject that request. | High | **Pass:** The request appears in the patient's pending list, and no records are accessible until the patient approves it. **Fail:** The clinic gets access before approval, or a request without a stated purpose is accepted. | Clinics need a formal way to ask for data. Stating the purpose and duration lets the patient make an informed decision. |
| FR-004 | Functional | The system shall check, on every record access attempt, that an active and unexpired consent covers the requesting clinic, the doctor and the requested record, and shall release only the records covered by that consent. | High | **Pass:** Access with a valid consent returns only the consented records; access with a missing, expired or revoked consent is denied with a reason. **Fail:** Any record is released without a matching active consent. | Consent has no value unless it is enforced at the point of access. This check is what prevents unauthorised disclosure. |
| FR-005 | Functional | The system shall allow a patient to view all their consents (active, expired and revoked) and the history of every access made to their records. | Medium | **Pass:** Each access made under a consent is listed with the clinic, doctor, record and timestamp. **Fail:** An access that took place is missing from the patient's history. | Transparency builds trust. Patients can see who viewed their data and can spot and report misuse. |

## Non-Functional Requirements

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|----|------|-------------|----------|---------------------|-----------|
| NFR-001 | Security (Auditability) | All consent grant, revoke and record access events shall be permanently written to an append-only audit trail. | High | **Pass:** Every grant, revoke and access event produces exactly one audit entry with actor, action, record scope and timestamp, and any attempt to edit or delete an entry is rejected. **Fail:** An event occurs without an audit entry, or an existing entry can be modified or deleted. | A tamper-proof trail is needed for legal compliance, for resolving disputes, and for investigating data breaches. |
| NFR-002 | Performance | The system shall complete consent validation for a record access request within 500 ms for 95% of requests under a load of 1,000 concurrent users. | Medium | **Pass:** A load test with 1,000 concurrent users shows a 95th percentile validation time of 500 ms or less. **Fail:** The 95th percentile validation time exceeds 500 ms under the same load. | Doctors access records during consultations. Slow consent checks would delay care and push staff towards unsafe workarounds. |
