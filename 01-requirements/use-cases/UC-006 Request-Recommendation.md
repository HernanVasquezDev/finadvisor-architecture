# UC-006 — Generate AI Financial Recommendation

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-006 |
| Name | Generate AI Financial Recommendation |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | AI Recommendation Service, Prompt Builder, Python AI Engine, PostgreSQL |
| Priority | Critical |
| Status | Draft |

---

# Goal

Generate an explainable and personalized financial recommendation based on the user's financial profile and one or more credit simulations.

---

# Description

This use case enables the platform to analyze a user's financial situation using Artificial Intelligence.

The system combines structured financial information with one or more credit simulations to generate a contextual recommendation that explains potential benefits, risks and alternative options.

The recommendation is intended to support financial decision-making and must never replace the user's judgment.

---

# Stakeholders

## Authenticated User

Wants to understand the financial consequences of a borrowing decision before committing to a loan.

---

## EasyCredit

Must provide transparent, responsible and explainable AI-assisted financial guidance.

---

## AI Recommendation Service

Must generate recommendations that are understandable, traceable and based on factual financial information.

---

# Preconditions

- The user is authenticated.
- A valid Financial Profile exists.
- At least one Credit Simulation exists.
- The AI Recommendation Service is available.
- The Prompt Builder Service is operational.

---

# Trigger

The user selects **Generate AI Recommendation**.

---

# Main Success Scenario

1. The user requests an AI recommendation.

2. The system retrieves the user's Financial Profile.

3. The system retrieves the selected Credit Simulation.

4. The system collects all relevant financial indicators.

5. The Prompt Builder constructs a structured prompt.

6. The prompt is sent to the Python AI Engine.

7. The AI Engine analyzes the financial information.

8. The AI Engine returns a structured recommendation.

9. The system validates the AI response format.

10. The recommendation is persisted.

11. The recommendation is associated with the originating simulation.

12. The system presents the recommendation to the user, including:

   - Executive summary
   - Affordability assessment
   - Risk analysis
   - Positive factors
   - Potential concerns
   - Alternative suggestions
   - Confidence level
   - Explanation of the reasoning

---

# Alternative Flows

## A1 — Multiple Simulations Selected

The user requests a recommendation based on multiple simulations.

The AI Engine evaluates all available scenarios and explains their differences.

---

## A2 — Existing Recommendation

A recommendation already exists for the selected simulation.

The user may:

- View the existing recommendation.
- Generate a new recommendation using updated financial information.

---

# Exception Flows

## E1 — AI Service Unavailable

The recommendation cannot be generated.

The user is informed that AI analysis is temporarily unavailable.

Previously generated simulations remain available.

---

## E2 — Invalid AI Response

The AI Engine returns an incomplete or invalid response.

The recommendation is discarded.

The incident is logged.

---

## E3 — Prompt Generation Failure

The Prompt Builder cannot generate a valid prompt.

The recommendation process is aborted.

---

## E4 — Persistence Failure

The recommendation cannot be stored.

The operation is rolled back.

The user receives an informative error.

---

# Postconditions

## Success

- A new AI Recommendation exists.
- The recommendation is linked to the originating simulation.
- The recommendation is available for future consultation.

---

## Failure

No recommendation is created.

Existing simulations remain unchanged.

---

# Business Rules

- BR-001 — Debt Capacity
- BR-002 — Financial Risk
- BR-003 — Recommendation Confidence
- BR-005 — Simulation Persistence
- BR-006 — Explainable AI

---

# Related Functional Requirements

- FR-AI-001
- FR-AI-002
- FR-AI-003

---

# Related User Stories

- US-AI-001
- US-AI-002

---

# Dependencies

This use case depends on:

- Authentication Module
- Financial Profile Service
- Simulation Service
- Prompt Builder Service
- AI Recommendation Service
- Recommendation Repository

---

# Related Domain Objects

- FinancialProfile
- CreditSimulation
- AIRecommendation
- RecommendationExplanation
- RecommendationConfidence
- FinancialRiskAssessment
- AffordabilityAssessment

---

# Security Considerations

- AI recommendations shall only be generated using the authenticated user's data.
- Sensitive financial information shall never be exposed through prompts beyond what is required.
- AI responses shall be validated before persistence.
- Personally identifiable information shall be minimized whenever possible.
- Every recommendation request shall be traceable for auditing purposes.

---

# Non-Functional Requirements

- NFR-AI-001
- NFR-AI-002
- NFR-AI-003
- NFR-AI-004
- NFR-REL-002
- NFR-SEC-003
- NFR-DATA-001
- NFR-TEST-002

---

# Related APIs

AI Recommendation

- POST /api/v1/recommendations
- GET /api/v1/recommendations/{recommendationId}
- GET /api/v1/simulations/{simulationId}/recommendation

---

# Future Extensions

Potential future enhancements include:

- Conversational AI financial advisor
- Personalized budgeting recommendations
- Loan refinancing suggestions
- Investment opportunity analysis
- Tax optimization guidance
- Multi-model AI consensus
- Recommendation versioning
- Continuous financial monitoring
- Proactive financial alerts

---

# Notes

This use case represents the core differentiator of EasyCredit.

The AI Recommendation Engine is an advisory component and shall never make financial decisions on behalf of the user.

All recommendations must be explainable, reproducible within the same input context and presented in language that is understandable to non-expert users.

Financial calculations remain deterministic and independent from AI-generated interpretations.