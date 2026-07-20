# UC-001 — Register User

## General Information

| Field | Value |
|--------|-------|
| Use Case ID | UC-001 |
| Name | Register User |
| Scope | EasyCredit |
| Level | User Goal |
| Primary Actor | Visitor |
| Supporting Actors | Authentication Service, PostgreSQL |
| Priority | Critical |
| Status | Draft |

---

# Goal

Allow a visitor to create a personal EasyCredit account in order to access personalized financial services.

---

# Description

This use case describes the process through which a visitor registers a new account within EasyCredit.

Successful registration creates a secure user identity that can later be used to authenticate, manage a financial profile and access personalized recommendations.

---

# Stakeholders

## Visitor

Wants to securely create an account.

---

## EasyCredit

Must ensure every account is unique and securely stored.

---

## Security

Requires passwords to be protected and user data handled securely.

---

# Preconditions

- The visitor is not authenticated.
- The registration service is available.
- Database connectivity is operational.

---

# Trigger

The visitor selects **Create Account**.

---

# Main Success Scenario

1. The visitor opens the registration page.

2. The system displays the registration form.

3. The visitor provides:

   - Email address
   - Password
   - Password confirmation

4. The visitor accepts the Terms of Service and Privacy Policy.

5. The visitor submits the form.

6. The system validates all provided information.

7. The system verifies that the email address does not already exist.

8. The password is securely hashed.

9. A new user account is created.

10. The system stores the new account.

11. The system confirms successful registration.

12. The visitor may proceed to authentication.

---

# Alternative Flows

## A1 — Email Already Registered

At step 7:

1. The system detects an existing account.

2. Registration is cancelled.

3. The visitor receives an informative validation message.

4. The visitor may retry with another email.

---

## A2 — Invalid Input

At step 6:

The system detects invalid information such as:

- Invalid email format
- Missing fields
- Password policy violation
- Password confirmation mismatch

The visitor is asked to correct the information.

---

# Exception Flows

## E1 — Database Unavailable

At any persistence step:

1. Registration is aborted.

2. No account is created.

3. The incident is logged.

4. The visitor receives a generic error message.

---

## E2 — Unexpected System Error

1. Registration is cancelled.

2. Partial information is discarded.

3. The error is logged.

4. The visitor is informed that registration could not be completed.

---

# Postconditions

## Success

- A new user account exists.
- Credentials are securely stored.
- The user can authenticate.

---

## Failure

No account is created.

---

# Business Rules

- BR-004 — Loan Validation *(Not Applicable)*
- BR-006 — Explainable AI *(Not Applicable)*

No business-specific financial rules apply during user registration.

Future authentication rules may introduce additional business constraints.

---

# Related Functional Requirements

- FR-AUTH-001
- FR-AUTH-002

---

# Related User Stories

- US-AUTH-001
- US-AUTH-002

---

# Security Considerations

- Passwords shall never be stored in plain text.
- Password hashing shall use BCrypt or a stronger algorithm.
- Email uniqueness shall be enforced.
- Sensitive validation errors shall not expose internal information.
- Secrets shall never be hardcoded.

---

# Non-Functional Requirements

- NFR-SEC-001
- NFR-SEC-002
- NFR-SEC-004
- NFR-REL-001
- NFR-MNT-001
- NFR-TEST-001

---

# Future Extensions

Possible future enhancements include:

- Email verification
- Multi-factor authentication (MFA)
- OAuth2 login
- Google authentication
- Microsoft authentication
- GitHub authentication
- Account activation workflow
- CAPTCHA
- Rate limiting

---

# Notes

Registration only creates a user identity.

No financial profile is created during this process.

Financial information is managed independently through **UC-003 — Manage Financial Profile**.