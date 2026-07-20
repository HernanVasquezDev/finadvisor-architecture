# UC-010 — Manage User Account

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-010 |
| Name | Manage User Account |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Authenticated User |
| Supporting Actors | User Account Service, Authentication Service, PostgreSQL |
| Priority | High |
| Status | Draft |

---

# Goal

Allow authenticated users to manage their account settings, security preferences and personal information while maintaining the integrity and security of their account.

---

# Description

This use case enables authenticated users to manage their EasyCredit account.

Users may update personal information, change their password, manage active sessions and configure account preferences.

The use case focuses exclusively on account management and does not modify the user's financial profile or financial data.

---

# Stakeholders

## Authenticated User

Wants to keep account information secure and up to date.

---

## EasyCredit

Must guarantee account integrity and protect user identity.

---

## Security

Requires secure authentication before performing sensitive account operations.

---

# Preconditions

- The user is authenticated.
- The account is active.
- Account Management Service is available.

---

# Trigger

The user opens **Account Settings**.

---

# Main Success Scenario

1. The user opens the Account Settings page.

2. The system retrieves the current account information.

3. The user selects one of the available actions:

   - Update personal information
   - Change password
   - View active sessions
   - Terminate active sessions
   - Configure notification preferences
   - Download personal data
   - Request account deletion

4. The system validates the submitted request.

5. The requested operation is executed.

6. The changes are persisted.

7. The system confirms the successful operation.

---

# Alternative Flows

## A1 — Change Password

The user provides:

- Current password
- New password
- Password confirmation

The system validates the credentials and updates the password.

---

## A2 — Update Personal Information

The user modifies editable account information such as:

- Full name
- Preferred language
- Time zone
- Notification preferences

The system validates and stores the changes.

---

## A3 — Manage Active Sessions

The user reviews active sessions and may revoke one or all sessions except the current one.

---

## A4 — Request Account Deletion

The user requests account deletion.

The system requires additional confirmation before scheduling the deletion process according to the platform's data retention policy.

---

# Exception Flows

## E1 — Invalid Password

The current password is incorrect.

The password change is rejected.

---

## E2 — Unauthorized Operation

The user attempts to perform an action without sufficient authorization.

Access is denied.

---

## E3 — Database Failure

The requested operation cannot be completed.

Changes are rolled back.

The user is notified.

---

# Postconditions

## Success

- The requested account changes have been applied.
- Security-sensitive operations have been recorded in the audit log.

---

## Failure

The account remains unchanged.

---

# Business Rules

- BR-006 — Explainable AI *(Not Applicable)*

No financial business rules apply to account management.

---

# Related Functional Requirements

- FR-ACCOUNT-001
- FR-ACCOUNT-002
- FR-ACCOUNT-003
- FR-ACCOUNT-004

---

# Related User Stories

- US-ACCOUNT-001
- US-ACCOUNT-002

---

# Dependencies

This use case depends on:

- Authentication Module
- Authorization Service
- User Account Service
- User Repository
- Audit Service

---

# Related Domain Objects

- User
- UserProfile
- Credential
- UserSession
- NotificationPreference
- AccountSettings

---

# Security Considerations

- Sensitive operations shall require authentication.
- Password changes shall require the current password.
- Active sessions shall be revocable.
- Account deletion shall require explicit confirmation.
- Every security-sensitive action shall be auditable.
- Personal data shall be handled in accordance with applicable privacy regulations.

---

# Non-Functional Requirements

- NFR-SEC-001
- NFR-SEC-002
- NFR-SEC-003
- NFR-DATA-001
- NFR-REL-001
- NFR-TEST-001

---

# Related APIs

User Account

- GET /api/v1/account
- PUT /api/v1/account
- PUT /api/v1/account/password
- GET /api/v1/account/sessions
- DELETE /api/v1/account/sessions/{sessionId}
- DELETE /api/v1/account

---

# Future Extensions

Potential future enhancements include:

- Multi-Factor Authentication (MFA)
- Passkeys (WebAuthn)
- Trusted devices
- Security activity timeline
- Privacy dashboard
- Account recovery workflow
- Data portability enhancements
- Personalized notification rules

---

# Notes

This use case is responsible only for managing the user's account and security settings.

Financial data, simulations and AI recommendations are managed independently through their corresponding use cases.

Account deletion should follow a configurable retention policy to support regulatory compliance, auditing requirements and recovery windows where applicable.