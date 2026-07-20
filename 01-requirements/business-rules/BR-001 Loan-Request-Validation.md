# BR-001 — Loan Request Validation

## General Information

| Field | Value |
|--------|-------|
| Business Rule ID | BR-001 |
| Name | Loan Request Validation |
| Category | Validation |
| Priority | Critical |
| Status | Active |

---

# Objective

Ensure that every credit simulation request complies with the minimum business requirements before financial calculations are performed.

---

# Context

Before a credit simulation can be executed, the platform must verify that the submitted request represents a valid and processable financial scenario.

This rule prevents invalid, incomplete or inconsistent loan requests from entering the credit analysis workflow.

---

# Rule Statement

Every loan request shall satisfy all mandatory business validation rules before a simulation is created.

If any validation rule fails, the simulation request shall be rejected.

---

# Business Rationale

Validating loan requests before processing ensures:

- Accurate financial calculations.
- Consistent business behavior.
- Reliable AI recommendations.
- Prevention of invalid financial scenarios.

---

# Validation Rules

The following conditions shall be satisfied:

- Loan amount must be greater than zero.
- Repayment period must be greater than zero.
- Interest rate must not be negative.
- Selected financial institution must exist.
- Selected financial institution must be active.
- Selected credit product must exist.
- Selected credit product must be active.
- Loan amount must be within the product's allowed range.
- Repayment period must be supported by the selected product.
- Required financial profile information must be available.

---

# Inputs

- Financial Profile
- Credit Product
- Financial Institution
- Loan Amount
- Repayment Period

---

# Outputs

Validation Result

Accepted

Rejected

Validation Errors

---

# Failure Handling

If validation fails:

- The simulation shall not be created.
- No financial calculations shall be executed.
- No AI recommendation shall be requested.
- Validation errors shall be returned to the user.

---

# Related Use Cases

- UC-004 — Perform Credit Simulation
- UC-005 — Compare Credit Simulations (Input validation)

---

# Related Functional Requirements

- FR-SIM-001
- FR-SIM-002

---

# Related Domain Objects

- CreditSimulation
- CreditProduct
- FinancialInstitution
- LoanAmount
- RepaymentPeriod

---

# Compliance

Every credit simulation must satisfy this business rule before entering the Simulation Engine.

---

# Future Considerations

Future versions may include:

- Regulatory validation
- Country-specific lending rules
- Credit score validation
- Open Banking verification
- Debt-to-Income eligibility validation