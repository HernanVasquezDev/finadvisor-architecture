# BR-005 — Affordability Assessment

## General Information

| Field | Value |
|--------|-------|
| Business Rule ID | BR-005 |
| Name | Affordability Assessment |
| Category | Financial Policy |
| Priority | Critical |
| Status | Active |

---

# Objective

Determine whether a proposed credit obligation is financially affordable for the user based on their current financial situation and the simulated loan conditions.

---

# Context

A loan may be mathematically valid while still being financially unsuitable for a specific user.

The platform shall evaluate affordability using the user's financial profile together with the projected loan obligations to determine whether the proposed credit represents a sustainable financial commitment.

This assessment serves as one of the primary decision inputs for financial simulations and AI-generated recommendations.

---

# Rule Statement

Every credit simulation shall include an Affordability Assessment.

The assessment shall be based on deterministic business rules and configurable financial policies.

Artificial Intelligence may explain the assessment but shall never determine affordability independently.

---

# Business Rationale

Evaluating affordability helps users avoid financial overcommitment and promotes responsible borrowing.

Providing a standardized affordability assessment also improves the consistency of simulations and the quality of AI-generated recommendations.

---

# Assessment Criteria

The affordability evaluation may consider, but is not limited to:

- Monthly income
- Monthly expenses
- Existing financial obligations
- Estimated monthly payment
- Disposable income
- Debt Capacity Assessment
- Financial Risk Assessment
- Loan amount
- Interest rate
- Repayment period

The weighting and thresholds of these criteria shall be configurable according to business policies.

---

# Affordability Levels

The platform shall classify affordability using configurable categories, such as:

- Affordable
- Borderline
- Not Affordable

Future versions may introduce additional classifications or institution-specific policies.

---

# Inputs

- Financial Profile
- Credit Simulation
- Debt Capacity Assessment
- Financial Risk Assessment
- Configurable Business Policies

---

# Outputs

Affordability Assessment

Including, where applicable:

- Affordability Level
- Supporting Indicators
- Contributing Factors
- Assessment Timestamp

---

# Failure Handling

If sufficient financial information is unavailable:

- An affordability assessment shall not be generated.
- The user shall be informed that additional financial information is required.
- AI recommendations shall clearly indicate the missing information.

---

# Related Use Cases

- UC-004 — Perform Credit Simulation
- UC-005 — Compare Credit Simulations
- UC-006 — Generate AI Financial Recommendation

---

# Related Functional Requirements

- FR-SIM-002
- FR-SIM-003
- FR-AI-001

---

# Related Domain Objects

- CreditSimulation
- FinancialProfile
- AffordabilityAssessment
- DebtCapacityAssessment
- FinancialRiskAssessment
- MonthlyPayment
- DisposableIncome

---

# Compliance

Every credit simulation shall include an Affordability Assessment before an AI recommendation is generated.

Affordability shall be reproducible for the same financial inputs and business policy configuration.

---

# Future Considerations

Future versions may incorporate:

- Institution-specific affordability models
- Country-specific regulatory thresholds
- Inflation-adjusted affordability
- Household-level affordability analysis
- Open Banking financial verification
- Dynamic affordability policies