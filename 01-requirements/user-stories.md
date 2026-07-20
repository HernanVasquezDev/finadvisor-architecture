# User Stories

## Project

EasyCredit

AI-Powered Credit Decision Platform

Version: 0.1

Status: Draft

---

# Introduction

This document describes the primary user stories for the Minimum Viable Product (MVP).

Each story represents a business capability from the user's perspective and is traceable to one or more functional requirements.

---

# Priority Legend

| Priority | Meaning |
|----------|---------|
| Must | Required for MVP |
| Should | Important |
| Could | Future enhancement |

---

# Epic 1 — Authentication

## US-AUTH-001

### User Story

As a visitor,

I want to create an account,

so that I can securely access personalized financial analyses.

### Business Value

Allows users to maintain a personal financial history.

### Acceptance Criteria

- User provides email and password.
- Email format is validated.
- Password meets security requirements.
- User account is created successfully.
- Duplicate emails are rejected.

### Related Requirements

- FR-AUTH-001

---

## US-AUTH-002

### User Story

As a registered user,

I want to log into the platform,

so that I can access my financial information.

### Related Requirements

- FR-AUTH-002
- FR-AUTH-003

---

# Epic 2 — Financial Profile

## US-PROFILE-001

### User Story

As an authenticated user,

I want to create my financial profile,

so that recommendations are personalized.

### Acceptance Criteria

The profile shall include:

- Income
- Expenses
- Existing debts
- Financial goals

### Related Requirements

- FR-PROFILE-001
- FR-PROFILE-002

---

# Epic 3 — Credit Simulation

## US-SIM-001

### User Story

As a user,

I want to simulate a loan,

so that I can estimate my monthly payment before borrowing.

### Acceptance Criteria

The system shall calculate:

- Monthly payment
- Total repayment
- Total interest
- Loan duration

### Related Requirements

- FR-SIM-001
- FR-SIM-002

---

## US-SIM-002

### User Story

As a user,

I want to compare multiple loan simulations,

so that I can identify the most suitable financial option.

### Related Requirements

- FR-SIM-004

---

## US-SIM-003

### User Story

As a user,

I want to save my simulations,

so that I can review them later.

### Related Requirements

- FR-SIM-005

---

# Epic 4 — AI Recommendations

## US-AI-001

### User Story

As a user,

I want to receive AI-generated recommendations,

so that I can better understand my borrowing options.

### Acceptance Criteria

Recommendations shall include:

- Risk analysis
- Financial explanation
- Suggested alternatives
- Plain language

### Related Requirements

- FR-AI-001
- FR-AI-002
- FR-AI-003

---

## US-AI-002

### User Story

As a user,

I want to understand why a recommendation was generated,

so that I can make my own financial decision.

### Related Requirements

- FR-AI-003

---

# Epic 5 — Financial Analysis

## US-ANALYSIS-001

### User Story

As a user,

I want to know whether I can safely afford a loan,

so that I avoid excessive debt.

### Related Requirements

- FR-ANALYSIS-001
- FR-ANALYSIS-002
- FR-ANALYSIS-003

---

# Epic 6 — Recommendation History

## US-HISTORY-001

### User Story

As a user,

I want to access previous simulations,

so that I can compare financial decisions over time.

### Related Requirements

- FR-HISTORY-001
- FR-HISTORY-002

---

# Epic 7 — Administration

## US-ADMIN-001

### User Story

As an administrator,

I want to manage financial institutions,

so that the platform provides updated information.

### Related Requirements

- FR-ADMIN-001

---

## US-ADMIN-002

### User Story

As an administrator,

I want to update financial products,

so that simulations remain accurate.

### Related Requirements

- FR-ADMIN-002
- FR-ADMIN-003

---

# Future User Stories

The following stories are intentionally postponed:

- Open Banking integration
- AI financial coaching
- Investment recommendations
- Insurance analysis
- Tax planning
- Retirement planning
- Credit score prediction
- Automatic bank synchronization

These capabilities belong to future product phases.