# UC-009 — Manage Financial Institutions

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-009 |
| Name | Manage Financial Institutions |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Administrator |
| Supporting Actors | Institution Management Service, PostgreSQL |
| Priority | High |
| Status | Draft |

---

# Goal

Allow authorized administrators to create, update, activate, deactivate and maintain financial institutions available within the EasyCredit platform.

---

# Description

This use case enables administrators to manage the catalog of financial institutions whose products may be used in credit simulations.

A Financial Institution represents an organization that offers one or more credit products compatible with EasyCredit.

Maintaining accurate institution information ensures users can perform realistic and up-to-date financial simulations.

---

# Stakeholders

## Administrator

Needs to maintain an accurate catalog of participating financial institutions.

---

## EasyCredit

Requires consistent institutional data for simulations and recommendations.

---

## End Users

Expect reliable information regarding financial institutions and their products.

---

# Preconditions

- The user is authenticated.
- The user has Administrator privileges.
- Institution Management Service is available.

---

# Trigger

The administrator selects **Financial Institutions** from the administration panel.

---

# Main Success Scenario

1. The administrator opens the Financial Institutions module.

2. The system displays all registered institutions.

3. The administrator selects one of the following actions:

   - Register a new institution
   - Update institution information
   - Activate an institution
   - Deactivate an institution
   - View institution details

4. The administrator enters or modifies institution information.

5. The system validates the submitted information.

6. The institution is persisted.

7. The system confirms the successful operation.

---

# Alternative Flows

## A1 — Register New Institution

A new financial institution is added to the catalog.

---

## A2 — Update Institution

The administrator modifies existing institution information.

---

## A3 — Deactivate Institution

The institution becomes unavailable for future simulations.

Existing simulations remain unaffected.

---

## A4 — Reactivate Institution

The institution becomes available again.

---

# Exception Flows

## E1 — Invalid Institution Information

Examples include:

- Missing institution name
- Invalid website
- Invalid contact information

Validation errors are displayed.

---

## E2 — Duplicate Institution

The institution already exists.

Registration is rejected.

---

## E3 — Database Failure

The requested operation is cancelled.

The administrator is notified.

---

# Postconditions

## Success

The institution catalog reflects the requested changes.

---

## Failure

The catalog remains unchanged.

---

# Business Rules

- BR-004 — Loan Validation

---

# Related Functional Requirements

- FR-ADMIN-001
- FR-ADMIN-002

---

# Related User Stories

- US-ADMIN-001

---

# Dependencies

This use case depends on:

- Authentication Module
- Authorization Service
- Institution Management Service
- Financial Institution Repository

---

# Related Domain Objects

- FinancialInstitution
- InstitutionStatus
- InstitutionContact
- InstitutionAddress
- InstitutionIdentifier

---

# Security Considerations

- Only administrators may manage financial institutions.
- Every administrative operation shall be auditable.
- Unauthorized access attempts shall be logged.
- Institution updates shall never affect historical simulations.

---

# Non-Functional Requirements

- NFR-SEC-003
- NFR-DATA-001
- NFR-MNT-001
- NFR-TEST-001

---

# Related APIs

Financial Institutions

- GET /api/v1/admin/institutions
- POST /api/v1/admin/institutions
- PUT /api/v1/admin/institutions/{institutionId}
- PATCH /api/v1/admin/institutions/{institutionId}/status
- GET /api/v1/admin/institutions/{institutionId}

---

# Future Extensions

Potential future enhancements include:

- Institution logo management
- Regulatory information
- Branch network
- Customer support channels
- Open Banking integration
- Product synchronization via APIs
- Institution ratings
- Regional availability

---

# Notes

Financial Institutions are reference entities within the platform.

Institution modifications affect only future operations.

Historical simulations always preserve the institution information that existed when the simulation was created through immutable snapshots.