# BR-002 — Debt Capacity Assessment

## General Information

| Field | Value |
|--------|-------|
| Business Rule ID | BR-002 |
| Name | Debt Capacity Assessment |
| Category | Financial Policy |
| Priority | Critical |
| Status | Active |

---

# Objective

Ensure that every credit simulation evaluates the user's repayment capacity before generating financial recommendations.

---

# Context

A credit simulation should not be based solely on loan conditions.

The user's current financial situation must also be considered to determine whether the proposed financial obligation is sustainable.

Debt Capacity Assessment helps identify situations where a new financial commitment could represent an excessive financial burden.

---

# Rule Statement

Every credit simulation shall evaluate the user's repayment capacity using the financial information available in the Financial Profile.

The resulting assessment shall be considered during affordability calculations and AI-generated recommendations.

Debt capacity thresholds shall be configurable and may vary according to business policies, financial institutions or credit products.

---

# Business Rationale

Responsible financial decisions require evaluating not only whether a loan can be approved, but also whether it can be reasonably sustained over time.

This rule promotes responsible borrowing, improves recommendation quality and helps users understand the financial implications of new debt.

---

# Assessment Criteria

The assessment may consider, but is not limited to:

- Monthly income
- Monthly expenses
- Existing debt obligations
- Estimated monthly payment
- Debt-to-Income Ratio (DTI)
- Disposable income
- Employment status
- Financial goals

The exact assessment formula is configurable and may evolve over time.

---

# Inputs

- Financial Profile
- Credit Simulation
- Monthly Payment
- Existing Debt
- Configurable Business Policies

---

# Outputs

Debt Capacity Assessment

Possible outcomes include:

- Low Financial Impact
- Moderate Financial Impact
- High Financial Impact

Additional indicators may include:

- Estimated Debt-to-Income Ratio
- Disposable Income
- Affordability Score

---

# Failure Handling

If sufficient financial information is unavailable:

- The debt capacity assessment shall not be performed.
- The user shall be informed that additional financial information is required.
- AI recommendations may be limited or unavailable.

---

# Related Use Cases

- UC-003 — Maintain Financial Profile
- UC-004 — Perform Credit Simulation
- UC-006 — Generate AI Financial Recommendation

---

# Related Functional Requirements

- FR-PROFILE-003
- FR-SIM-002
- FR-AI-001

---

# Related Domain Objects

- FinancialProfile
- CreditSimulation
- DebtCapacityAssessment
- MonthlyIncome
- MonthlyExpense
- ExistingDebt
- MonthlyPayment

---

# Compliance

Debt Capacity Assessment shall always be performed before generating an AI financial recommendation.

---

# Future Considerations

Future versions may incorporate:

- Credit bureau integration
- Open Banking data
- Dynamic affordability models
- Institution-specific assessment policies
- Machine Learning-assisted affordability estimation
- Country-specific regulatory requirements