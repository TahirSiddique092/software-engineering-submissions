# Lab 1: Use-Case Flow Specification

**Problem Statement #13:** Patient Health Record Consent Management System

**Name:** Mohammed Tahir Siddique | **SRN:** PES2UG24AM092

## UC-01: Grant Time-Bound Consent

| Field | Details |
|-------|---------|
| Use Case ID | UC-01 |
| Use Case Name | Grant Time-Bound Consent |
| Primary Actor | Patient |
| Other Stakeholder | Clinic Administrator (the clinic receives the access) |
| Description | The patient gives a verified clinic doctor access to selected health records for a limited period of time. |
| Related Requirements | FR-001, FR-004, NFR-001 |
| Included Use Case | Log Audit Event |

### Preconditions

1. The patient is registered and logged in to the system.
2. The patient has at least one health record stored in the system.
3. The clinic is registered, and the doctor has been verified by the clinic administrator.

### Postconditions

1. An active consent exists with the selected records, the recipient doctor and an expiry timestamp.
2. The clinic can access only the selected records until the expiry timestamp.
3. The grant event is written to the append-only audit trail.
4. The clinic administrator is notified that access has been granted.

### Main Success Scenario

| Step | Actor | Action |
|------|-------|--------|
| 1 | Patient | Selects the "Grant Consent" option. |
| 2 | System | Displays the patient's records and the list of registered clinics. |
| 3 | Patient | Selects the clinic and a verified doctor of that clinic. |
| 4 | Patient | Selects the specific records to share. |
| 5 | Patient | Selects the access duration (for example, 24 hours). |
| 6 | System | Shows a summary with the recipient, the records and the expiry date and time. |
| 7 | Patient | Confirms the consent. |
| 8 | System | Creates the consent with status "Active" and stores the expiry timestamp. |
| 9 | System | Writes the grant event to the audit trail. |
| 10 | System | Notifies the clinic administrator and shows a confirmation to the patient. |

### Alternate Flow A1: Selected doctor is not verified

This flow starts at step 3 of the main success scenario.

| Step | Actor | Action |
|------|-------|--------|
| 3a | System | Detects that the selected doctor is not verified, or that the verification has been withdrawn. |
| 3b | System | Shows the message "This doctor is not verified. Consent cannot be granted." |
| 3c | Patient | Selects a different verified doctor, and the flow continues from step 4. |
| 3d | Patient | Otherwise cancels the operation. No consent is created and the use case ends. |
