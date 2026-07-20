# UC-008 — Manage Financial Products

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-008 |
| Name | Manage Credit Products |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Administrator |
| Supporting Actors | Product Management Service, PostgreSQL |
| Priority | High |
| Status | Draft |

---

# Goal

Allow authorized administrators to create, update, activate, deactivate and maintain credit products available for financial simulations.

---

# Description

This use case enables administrators to manage the catalog of credit products offered through EasyCredit.

Each credit product defines the financial characteristics required by the simulation engine, including interest rates, repayment limits, eligibility constraints and associated fees.

Maintaining an accurate product catalog ensures that all financial simulations are based on current and valid financial information.

---

# Stakeholders

## Administrator

Needs to maintain an up-to-date catalog of available credit products.

---

## EasyCredit

Requires reliable product information to generate accurate simulations.

---

## End Users

Expect simulations based on current financial products.

---

# Preconditions

- The user is authenticated.
- The user has Administrator privileges.
- Product Management Service is available.

---

# Trigger

The administrator selects **Credit Products** from the administration panel.

---

# Main Success Scenario

1. The administrator opens the Credit Products module.

2. The system displays the current product catalog.

3. The administrator chooses one of the following actions:

   - Create a new product
   - Update an existing product
   - Activate a product
   - Deactivate a product
   - View product details

4. The administrator enters or modifies product information.

5. The system validates the submitted information.

6. The product is persisted.

7. The system confirms the successful operation.

---

# Alternative Flows

## A1 — Create New Product

A new credit product is added to the catalog.

---

## A2 — Update Existing Product

The selected product information is modified.

---

## A3 — Deactivate Product

The product becomes unavailable for future simulations.

Existing simulations remain unaffected.

---

## A4 — Reactivate Product

A previously inactive product becomes available again.

---

# Exception Flows

## E1 — Invalid Product Information

Examples include:

- Negative interest rate
- Invalid repayment limits
- Missing required fields

Validation errors are displayed.

---

## E2 — Product Already Exists

A duplicate product is detected.

The operation is cancelled.

---

## E3 — Database Failure

The requested operation is rolled back.

The administrator is notified.

---

# Postconditions

## Success

The product catalog reflects the requested changes.

---

## Failure

The catalog remains unchanged.

---

# Business Rules

- BR-004 — Loan Validation

---

# Related Functional Requirements

- FR-ADMIN-002
- FR-ADMIN-003

---

# Related User Stories

- US-ADMIN-002

---

# Dependencies

This use case depends on:

- Authentication Module
- Authorization Service
- Product Management Service
- Credit Product Repository

---

# Related Domain Objects

- CreditProduct
- InterestRate
- RepaymentTerm
- LoanLimit
- ProductFee
- ProductStatus

---

# Security Considerations

- Only administrators may manage credit products.
- Every modification shall be auditable.
- Unauthorized access attempts shall be logged.
- Product changes shall not invalidate historical simulations.

---

# Non-Functional Requirements

- NFR-SEC-003
- NFR-DATA-001
- NFR-MNT-001
- NFR-TEST-001

---

# Related APIs

Credit Products

- GET /api/v1/admin/products
- POST /api/v1/admin/products
- PUT /api/v1/admin/products/{productId}
- PATCH /api/v1/admin/products/{productId}/status
- GET /api/v1/admin/products/{productId}

---

# Future Extensions

Potential future enhancements include:

- Product versioning
- Promotional interest rates
- Regional product availability
- Scheduled product activation
- Product approval workflow
- Bulk import/export
- Regulatory compliance validation

---

# Notes

Credit Products are reference data used by the Simulation Engine.

Updating a product affects only future simulations.

Previously generated simulations remain immutable and continue to reference the product configuration that existed at the time they were created.