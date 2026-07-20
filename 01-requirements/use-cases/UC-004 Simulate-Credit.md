# UC-004 — Perform Credit Simulation

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-004 |
| Name | Perform Credit Simulation |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | Simulation Service, Financial Institution Repository, Credit Product Repository, Calculation Engine, PostgreSQL |
| Priority | Critical |
| Status | Draft |

---

# Goal

Allow an authenticated user to perform a complete credit simulation based on their financial profile and a selected financial product in order to evaluate affordability, repayment conditions and overall borrowing impact.

---

# Description

This use case enables users to simulate a credit product before making any financial commitment.

The system combines user financial information, product characteristics and financial calculations to generate a realistic repayment scenario.

The resulting simulation becomes the basis for later AI-assisted recommendations and product comparisons.

---

# Stakeholders

## Authenticated User

Wants to understand the financial impact of acquiring a new credit.

---

## EasyCredit

Must provide accurate, transparent and deterministic financial simulations.

---

## AI Recommendation Engine

Consumes simulation results to generate personalized recommendations.

---

# Preconditions

- The user is authenticated.
- A valid Financial Profile exists.
- At least one Financial Institution is available.
- At least one Credit Product is available.
- Financial parameters are up to date.

---

# Trigger

The user selects **New Credit Simulation**.

---

# Main Success Scenario

1. The user opens the Credit Simulation page.

2. The system retrieves the user's Financial Profile.

3. The system displays the available Financial Institutions.

4. The user selects a Financial Institution.

5. The system displays the available Credit Products.

6. The user selects a Credit Product.

7. The user enters the desired loan amount.

8. The user selects the repayment period.

9. The user reviews additional configurable parameters, if applicable.

10. The user submits the simulation request.

11. The system validates all provided information.

12. The Calculation Engine performs all financial calculations.

13. The system generates:

   - Monthly payment
   - Total repayment
   - Total interest
   - Amortization schedule
   - Debt-to-income estimation
   - Affordability estimation

14. The simulation is persisted.

15. The system assigns a unique Simulation Identifier.

16. The user receives the completed simulation results.

17. The simulation becomes available for AI recommendation generation.

---

# Alternative Flows

## A1 — Existing Simulation Parameters

The user loads parameters from a previous simulation.

The system pre-populates the simulation form.

---

## A2 — Optional Parameters

Certain products require additional information such as:

- Down payment
- Grace period
- Insurance
- Administrative fees

The system requests only the information required by the selected product.

---

## A3 — Product Availability Changes

The selected product is no longer available.

The system requests a new product selection.

---

# Exception Flows

## E1 — Invalid Financial Information

Examples include:

- Loan amount ≤ 0
- Invalid repayment period
- Missing mandatory information
- Unsupported financial product

The system rejects the simulation request.

---

## E2 — Financial Calculation Failure

The Calculation Engine cannot complete the simulation.

No simulation is stored.

The incident is logged.

---

## E3 — Persistence Failure

The simulation cannot be saved.

The user receives an informative error.

The operation is rolled back.

---

# Postconditions

## Success

- A Simulation has been successfully created.
- Financial calculations are available.
- The simulation is persisted.
- The simulation may be used by UC-005 and UC-006.

---

## Failure

No Simulation is created.

---

# Business Rules

- BR-001 — Debt Capacity
- BR-002 — Financial Risk
- BR-004 — Loan Validation
- BR-005 — Simulation Persistence

---

# Related Functional Requirements

- FR-SIM-001
- FR-SIM-002
- FR-SIM-003
- FR-SIM-005

---

# Related User Stories

- US-SIM-001
- US-SIM-003

---

# Dependencies

This use case depends on:

- Authentication Module
- Financial Profile Service
- Simulation Service
- Calculation Engine
- Financial Institution Repository
- Credit Product Repository
- Simulation Repository

---

# Related Domain Objects

- User
- FinancialProfile
- CreditSimulation
- CreditProduct
- FinancialInstitution
- LoanAmount
- InterestRate
- RepaymentPeriod
- AmortizationSchedule
- MonthlyPayment

---

# Security Considerations

- Users may only create simulations for their own financial profile.
- Financial information shall never be exposed to other users.
- Financial calculations shall be deterministic.
- Sensitive financial data shall not appear in logs.
- Every simulation shall be traceable.

---

# Non-Functional Requirements

- NFR-PERF-001
- NFR-REL-001
- NFR-DATA-001
- NFR-DATA-002
- NFR-MNT-001
- NFR-TEST-001

---

# Related APIs

Simulation

- POST /api/v1/simulations
- GET /api/v1/simulations/{simulationId}
- GET /api/v1/simulations

---

# Future Extensions

Potential future enhancements include:

- Adjustable interest rates
- Balloon payments
- Early repayment simulation
- Loan refinancing
- Multi-currency simulations
- Inflation-adjusted projections
- Scenario comparison
- Sensitivity analysis
- Monte Carlo risk simulation
- Open Banking data integration

---

# Notes

A Credit Simulation represents an immutable financial analysis generated at a specific point in time.

Simulations are never modified after creation. New analyses produce new Simulation instances, ensuring traceability, auditability and historical consistency.

The output of this use case serves as the primary input for:

- UC-005 — Compare Credit Products
- UC-006 — Request AI Recommendation