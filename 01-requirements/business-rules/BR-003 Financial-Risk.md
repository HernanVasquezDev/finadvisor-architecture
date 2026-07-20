# BR-003 — Financial Risk Assessment

## General Information

| Field | Value |
|--------|-------|
| Business Rule ID | BR-003 |
| Name | Financial Risk Assessment |
| Category | Financial Policy |
| Priority | Critical |
| Status | Active |

---

# Objective

Ensure that every credit simulation includes a deterministic assessment of the user's financial risk before AI-generated recommendations are produced.

---

# Context

Financial decisions should not rely exclusively on loan conditions or repayment calculations.

The platform must evaluate the user's overall financial situation to identify potential risk factors that could affect the sustainability of a new financial obligation.

The Financial Risk Assessment provides a standardized business evaluation that serves as an input for simulations, affordability analysis and AI-assisted recommendations.

---

# Rule Statement

Every credit simulation shall include a Financial Risk Assessment generated through deterministic business rules.

Risk assessments shall be based on objective financial information and configurable business policies.

Artificial Intelligence may explain or contextualize the assessment but shall never replace or modify the underlying business evaluation.

---

# Business Rationale

A standardized financial risk assessment promotes responsible lending, improves consistency across simulations and increases user confidence in the platform's recommendations.

Separating deterministic risk evaluation from AI interpretation also improves traceability, explainability and regulatory compliance.

---

# Assessment Criteria

The assessment may consider, but is not limited to:

- Monthly income
- Monthly expenses
- Existing debt obligations
- Debt-to-Income Ratio (DTI)
- Disposable income
- Estimated monthly payment
- Employment status
- Loan amount
- Repayment period
- Interest rate
- Financial goals

The weighting of each criterion shall be configurable according to business policies.

---

# Risk Classification

The assessment shall classify financial risk into configurable categories, such as:

- Low Risk
- Moderate Risk
- High Risk

Additional classifications may be introduced in future versions.

---

# Inputs

- Financial Profile
- Credit Simulation
- Debt Capacity Assessment
- Business Policy Configuration

---

# Outputs

Financial Risk Assessment

Including, where applicable:

- Risk Level
- Risk Factors
- Supporting Indicators
- Assessment Timestamp

---

# Failure Handling

If sufficient financial information is unavailable:

- A Financial Risk Assessment shall not be generated.
- The user shall be informed that additional financial information is required.
- AI recommendations may be unavailable or explicitly marked as incomplete.

---

# Related Use Cases

- UC-003 — Maintain Financial Profile
- UC-004 — Perform Credit Simulation
- UC-006 — Generate AI Financial Recommendation
- UC-007 — Review Recommendation History

---

# Related Functional Requirements

- FR-PROFILE-003
- FR-SIM-002
- FR-AI-001
- FR-AI-002

---

# Related Domain Objects

- FinancialProfile
- CreditSimulation
- FinancialRiskAssessment
- DebtCapacityAssessment
- RiskFactor
- RiskLevel

---

# Compliance

Financial Risk Assessment shall be completed before an AI recommendation is generated.

AI-generated recommendations shall reference, but never alter, the business risk assessment.

---

# Future Considerations

Future versions may incorporate:

- Regulatory risk policies
- Institution-specific risk models
- Credit bureau integration
- Open Banking financial indicators
- Behavioral financial metrics
- Configurable scoring models
- Country-specific compliance rules