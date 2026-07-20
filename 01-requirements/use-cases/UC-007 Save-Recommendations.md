# UC-007 — Review Recommendation History

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-007 |
| Name | Review Recommendation History |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | Recommendation Service, PostgreSQL |
| Priority | High |
| Status | Draft |

---

# Goal

Allow authenticated users to review previously generated AI financial recommendations, understand past analyses and revisit historical financial decisions.

---

# Description

This use case enables users to access their historical AI-generated recommendations together with the associated financial simulations.

Users may review previous analyses, compare recommendations generated over time and better understand how changes in their financial situation affect AI-assisted guidance.

This use case promotes informed financial decision-making through historical traceability.

---

# Stakeholders

## Authenticated User

Wants to review previous financial analyses before making new financial decisions.

---

## EasyCredit

Must preserve recommendation history and ensure historical consistency.

---

## AI Recommendation Service

Provides historical recommendations for consultation only.

No new recommendation is generated during this use case.

---

# Preconditions

- The user is authenticated.
- At least one recommendation exists for the authenticated user.
- Recommendation Service is available.

---

# Trigger

The user selects **Recommendation History**.

---

# Main Success Scenario

1. The user opens the Recommendation History page.

2. The system retrieves all recommendations belonging to the authenticated user.

3. The system displays a chronological list of recommendations.

4. The user selects one recommendation.

5. The system retrieves the associated Credit Simulation.

6. The system displays the complete recommendation, including:

   - Executive summary
   - Financial context
   - Affordability assessment
   - Risk analysis
   - Positive factors
   - Potential concerns
   - Alternative suggestions
   - Confidence level
   - Recommendation date

7. The user reviews the recommendation.

8. The user may navigate back to the recommendation list.

---

# Alternative Flows

## A1 — Filter Recommendation History

The user filters recommendations by:

- Date
- Financial Institution
- Credit Product
- Recommendation Confidence
- Risk Level

The system displays the filtered results.

---

## A2 — Search Recommendation History

The user performs a keyword search.

Matching recommendations are displayed.

---

## A3 — Open Related Credit Simulation

The user chooses to view the Credit Simulation associated with the recommendation.

The system opens the related simulation.

---

# Exception Flows

## E1 — Recommendation Not Found

The selected recommendation no longer exists.

The system informs the user.

---

## E2 — Unauthorized Access

The requested recommendation belongs to another user.

Access is denied.

The incident is logged.

---

## E3 — Database Unavailable

Recommendation history cannot be retrieved.

The user receives a generic error message.

---

# Postconditions

## Success

- Historical recommendations have been successfully consulted.
- No recommendation data has been modified.

---

## Failure

No historical information is displayed.

---

# Business Rules

- BR-005 — Simulation Persistence
- BR-006 — Explainable AI

---

# Related Functional Requirements

- FR-HISTORY-001
- FR-HISTORY-002
- FR-HISTORY-003

---

# Related User Stories

- US-HISTORY-001

---

# Dependencies

This use case depends on:

- Authentication Module
- Recommendation Service
- Recommendation Repository
- Simulation Repository

---

# Related Domain Objects

- AIRecommendation
- CreditSimulation
- RecommendationHistory
- RecommendationConfidence
- FinancialRiskAssessment
- AffordabilityAssessment

---

# Security Considerations

- Users shall only access their own recommendation history.
- Historical recommendations shall remain immutable.
- Sensitive financial information shall never be exposed to unauthorized users.
- Every access shall be authenticated and authorized.

---

# Non-Functional Requirements

- NFR-DATA-002
- NFR-DATA-003
- NFR-REL-001
- NFR-MNT-001
- NFR-TEST-001

---

# Related APIs

Recommendation History

- GET /api/v1/recommendations
- GET /api/v1/recommendations/{recommendationId}
- GET /api/v1/recommendations/search

---

# Future Extensions

Potential future enhancements include:

- Timeline visualization
- Recommendation comparison
- AI recommendation evolution
- Recommendation export (PDF)
- Recommendation sharing
- Favorite recommendations
- Recommendation tagging
- Financial milestone tracking

---

# Notes

Recommendation History provides historical transparency but does not modify existing recommendations.

Every recommendation represents the AI interpretation of the user's financial context at a specific point in time.

Historical recommendations remain immutable to preserve traceability, auditability and explainability.

If the user's financial profile changes, a new recommendation should be generated instead of modifying an existing one.