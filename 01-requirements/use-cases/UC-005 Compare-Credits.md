# UC-005 — Compare Credit Simulations

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-005 |
| Name | Compare Credit Simulations |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | Simulation Service, Comparison Engine |
| Priority | High |
| Status | Draft |

---

# Goal

Allow users to compare multiple credit simulations in order to identify the financial alternative that best matches their personal circumstances and financial goals.

---

# Description

This use case enables users to evaluate two or more previously generated credit simulations side by side.

The comparison highlights relevant financial indicators, allowing users to understand the advantages and disadvantages of each borrowing alternative before making a financial decision.

The comparison itself does not generate recommendations.

Its purpose is to provide transparent financial information that can later be interpreted by the AI Recommendation Engine.

---

# Stakeholders

## Authenticated User

Wants to evaluate multiple borrowing alternatives objectively.

---

## EasyCredit

Must present financial information consistently and accurately.

---

## AI Recommendation Engine

May later consume comparison results when generating recommendations.

---

# Preconditions

- The user is authenticated.
- At least two valid credit simulations exist.
- The selected simulations belong to the authenticated user.

---

# Trigger

The user selects **Compare Simulations**.

---

# Main Success Scenario

1. The user opens the Simulation History.

2. The system displays available simulations.

3. The user selects two or more simulations.

4. The user requests a comparison.

5. The system retrieves all selected simulations.

6. The Comparison Engine validates compatibility.

7. The system calculates comparable financial indicators.

8. The system generates a comparison matrix including:

   - Loan amount
   - Interest rate
   - Monthly payment
   - Total repayment
   - Total interest
   - Loan duration
   - Debt-to-income ratio
   - Affordability estimation

9. The comparison results are displayed.

10. The user may continue to request an AI recommendation.

---

# Alternative Flows

## A1 — Compare Different Financial Institutions

The selected simulations belong to different financial institutions.

The comparison proceeds normally.

---

## A2 — Compare Different Loan Products

The selected simulations correspond to different credit products.

The comparison proceeds normally.

---

## A3 — Compare Historical Simulations

Previously created simulations may be compared regardless of creation date.

---

# Exception Flows

## E1 — Less Than Two Simulations Selected

The comparison cannot continue.

The user is asked to select additional simulations.

---

## E2 — Simulation Not Found

One or more selected simulations no longer exist.

The comparison is cancelled.

---

## E3 — Unauthorized Simulation

The user attempts to compare a simulation owned by another user.

Access is denied.

The incident is logged.

---

# Postconditions

## Success

- A comparison result has been generated.
- Original simulations remain unchanged.

---

## Failure

No comparison is produced.

---

# Business Rules

- BR-001 — Debt Capacity
- BR-002 — Financial Risk
- BR-005 — Simulation Persistence

---

# Related Functional Requirements

- FR-SIM-004
- FR-HISTORY-001
- FR-HISTORY-003

---

# Related User Stories

- US-SIM-002
- US-HISTORY-001

---

# Dependencies

This use case depends on:

- Authentication Module
- Simulation Service
- Comparison Engine
- Simulation Repository

---

# Related Domain Objects

- CreditSimulation
- ComparisonResult
- FinancialIndicator
- LoanAmount
- InterestRate
- MonthlyPayment
- DebtToIncomeRatio
- Affordability

---

# Security Considerations

- Users may compare only their own simulations.
- Financial information shall remain isolated between users.
- Original simulations shall never be modified during comparison.

---

# Non-Functional Requirements

- NFR-PERF-001
- NFR-DATA-001
- NFR-DATA-002
- NFR-TEST-001
- NFR-MNT-001

---

# Related APIs

Simulation Comparison

- POST /api/v1/simulations/compare

---

# Future Extensions

Potential future enhancements include:

- Unlimited simulation comparison
- Graphical comparison
- Sensitivity analysis
- What-if analysis
- Comparison templates
- AI-assisted comparison
- Export to PDF
- Export to Excel
- Comparison sharing

---

# Notes

This use case is intentionally independent from the AI Recommendation Engine.

Its responsibility is limited to generating objective financial comparisons.

Interpretation and recommendation are delegated to UC-006 — Request AI Recommendation.