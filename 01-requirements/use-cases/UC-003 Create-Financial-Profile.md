# UC-003 — Create Financial Profile

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-003 |
| Name | Create Financial Profile |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | Financial Profile Service, PostgreSQL |
| Priority | Critical |
| Status | Draft |

---

# Goal

Allow authenticated users to create and maintain an accurate financial profile that serves as the foundation for personalized financial simulations and AI-powered recommendations.

---

# Description

This use case enables authenticated users to create, update and maintain their personal financial information.

The financial profile represents the user's current financial situation and is used throughout the platform to generate realistic simulations, affordability analyses and personalized recommendations.

A complete and up-to-date financial profile is essential for ensuring the accuracy and relevance of the platform's financial insights.

---

# Stakeholders

## Authenticated User

Wants recommendations that accurately reflect their financial situation.

---

## EasyCredit

Requires reliable financial information to generate trustworthy analyses.

---

## AI Recommendation Engine

Depends on accurate financial data to produce personalized and explainable recommendations.

---

# Preconditions

- The user is authenticated.
- The user's account is active.
- Financial Profile Service is available.
- Database connectivity is operational.

---

# Trigger

The user selects **Financial Profile** from the application dashboard.

---

# Main Success Scenario

1. The user opens the Financial Profile section.

2. The system retrieves the current financial profile, if one exists.

3. The user reviews the existing information or starts a new profile.

4. The user provides or updates the following information:

   - Monthly income
   - Monthly expenses
   - Existing debts
   - Employment status
   - Financial goals

5. The system validates all submitted information.

6. The system calculates derived financial indicators required by the platform.

7. The financial profile is created or updated.

8. The system stores the financial profile.

9. The system confirms that the profile has been successfully saved.

---

# Alternative Flows

## A1 — Existing Financial Profile

At step 2:

1. The system loads the existing profile.

2. The user modifies one or more fields.

3. The updated profile replaces the previous version according to the profile versioning strategy.

---

## A2 — Partial Update

The user updates only selected financial information.

Only modified fields are validated and persisted.

---

# Exception Flows

## E1 — Invalid Financial Information

At validation:

Examples include:

- Negative income
- Negative expenses
- Invalid debt values
- Missing required information

The system displays validation errors and requests corrections.

---

## E2 — Database Unavailable

1. The profile is not stored.

2. No partial updates are persisted.

3. The incident is logged.

4. The user receives a generic error message.

---

## E3 — Unexpected System Failure

1. The operation is cancelled.

2. Changes are discarded.

3. The failure is logged.

4. The user is notified.

---

# Postconditions

## Success

- A valid financial profile exists.
- The profile is available for simulations.
- The profile is available for AI recommendations.

---

## Failure

The previously stored profile remains unchanged.

---

# Business Rules

- BR-001 — Debt Capacity
- BR-002 — Financial Risk
- BR-005 — Simulation Persistence (Future dependency)

---

# Related Functional Requirements

- FR-PROFILE-001
- FR-PROFILE-002
- FR-PROFILE-003

---

# Related User Stories

- US-PROFILE-001

---

# Dependencies

This use case depends on:

- Authentication Module
- Financial Profile Service
- Validation Service
- User Repository
- Financial Profile Repository

---

# Related Domain Objects

- User
- FinancialProfile
- Income
- Expense
- Debt
- FinancialGoal
- EmploymentStatus
- Currency

---

# Security Considerations

- Financial information shall only be accessible by its owner.
- Sensitive financial data shall never be exposed through logs.
- User authorization shall be verified before every update.
- Financial data shall be transmitted securely.
- Unauthorized modifications shall be rejected.

---

# Non-Functional Requirements

- NFR-SEC-003
- NFR-DATA-001
- NFR-DATA-003
- NFR-MNT-001
- NFR-TEST-001
- NFR-REL-001

---

# Related APIs

Financial Profile

- GET /api/v1/profile
- POST /api/v1/profile
- PUT /api/v1/profile

---

# Future Extensions

Potential future enhancements include:

- Multiple income sources
- Passive income tracking
- Asset management
- Investment portfolio
- Credit score integration
- Household financial profile
- Family budget management
- Automatic financial synchronization through Open Banking
- Financial document import
- Historical financial profile snapshots

---

# Notes

The Financial Profile is the primary source of user financial information throughout the platform.

Credit simulations, affordability analysis and AI-generated recommendations rely on the information maintained by this use case.

An incomplete or outdated profile may reduce the accuracy of financial recommendations.