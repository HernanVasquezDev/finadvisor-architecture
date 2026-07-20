# UC-002 — Login

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-002 |
| Name | Login |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Registered User |
| Supporting Actors | Authentication Service, PostgreSQL |
| Priority | Critical |
| Status | Draft |

---

# Goal

Allow a registered user to authenticate securely and access personalized EasyCredit services.

---

# Description

This use case describes the authentication process for registered users.

After successful authentication, the system establishes an authenticated session by issuing a secure access token, allowing the user to access protected resources such as financial profiles, simulations and AI-powered recommendations.

---

# Stakeholders

## Registered User

Wants secure and reliable access to personal financial information.

---

## EasyCredit

Must authenticate users securely while protecting sensitive information.

---

## Security

Requires strong authentication mechanisms and secure credential handling.

---

# Preconditions

- The user account exists.
- The account is active.
- Authentication services are available.
- Database connectivity is operational.

---

# Trigger

The user selects **Sign In**.

---

# Main Success Scenario

1. The user opens the login page.

2. The system displays the authentication form.

3. The user enters:

   - Email address
   - Password

4. The user submits the authentication request.

5. The system validates the request format.

6. The system searches for the user account.

7. The system verifies the provided password against the stored password hash.

8. Authentication succeeds.

9. The system generates an access token.

10. The system records the authentication event.

11. The authenticated session is established.

12. The user is redirected to the dashboard.

---

# Alternative Flows

## A1 — Invalid Credentials

At step 7:

1. Authentication fails.

2. No session is created.

3. The system displays a generic authentication error.

---

## A2 — Inactive Account

At step 6:

1. The account is found but marked as inactive.

2. Authentication is rejected.

3. The user receives an informative message.

---

## A3 — Expired Session

When accessing protected resources:

1. The system detects an expired token.

2. Authentication is requested again.

---

# Exception Flows

## E1 — Authentication Service Unavailable

1. Authentication is interrupted.

2. No session is created.

3. The incident is logged.

4. The user receives a generic error message.

---

## E2 — Database Unavailable

1. Authentication cannot continue.

2. The request is aborted.

3. The error is logged.

4. The user is informed that the service is temporarily unavailable.

---

# Postconditions

## Success

- The user is authenticated.
- A secure access token has been issued.
- An authenticated session exists.
- Authentication is recorded for auditing purposes.

---

## Failure

- No authenticated session exists.
- No access token is generated.

---

# Business Rules

No domain-specific financial rules apply during authentication.

Future authentication policies (MFA, account lockout, password expiration) may introduce additional business rules.

---

# Related Functional Requirements

- FR-AUTH-002
- FR-AUTH-003
- FR-AUTH-004

---

# Related User Stories

- US-AUTH-002

---

# Dependencies

This use case depends on:

- Authentication Module
- User Repository
- Password Encoder
- JWT Provider
- Validation Service
- Audit Service

---

# Related Domain Objects

- User
- Credential
- Email
- Password
- AuthenticationToken
- UserSession

---

# Security Considerations

- Passwords shall never be exposed.
- Authentication failures shall not reveal whether the email exists.
- JWT tokens shall have configurable expiration.
- Refresh tokens shall be supported in future versions.
- Authentication events shall be logged.
- Session tokens shall be invalidated after logout.
- Sensitive information shall never appear in logs.

---

# Non-Functional Requirements

- NFR-SEC-001
- NFR-SEC-002
- NFR-SEC-004
- NFR-REL-001
- NFR-TEST-001
- NFR-TEST-002
- NFR-OBS-002

---

# Future Extensions

Potential future enhancements include:

- Refresh Tokens
- Multi-Factor Authentication (MFA)
- OAuth2 Authentication
- Google Sign-In
- Microsoft Sign-In
- GitHub Sign-In
- Biometric Authentication (Mobile)
- Device Recognition
- Account Lockout Policy
- Password Expiration Policy
- Adaptive Authentication
- Risk-Based Authentication

---

# Notes

Authentication only establishes the user's identity and grants access to protected resources.

Financial information is not loaded or modified as part of this use case.

After successful authentication, users may continue with:

- UC-003 — Manage Financial Profile
- UC-004 — Simulate Credit
- UC-005 — Compare Credit Products
- UC-006 — Request AI Recommendation