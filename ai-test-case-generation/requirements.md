# Sample Requirements — AI Test Case Generation
**Tester:** Fatima Alfred  
**Date:** April 2026  
**Purpose:** This document contains the sample requirements used as input 
to ChatGPT to generate test cases. The AI output was then compared against 
manually written test cases to evaluate quality and coverage.

---

## Requirement 1 — Login Page

**Feature:** User Login  
**Description:** Users must be able to log in to the application using a 
registered email address and password.

**Acceptance Criteria:**
- Valid email and password combination must grant access
- Invalid credentials must display a clear error message
- Password field must be masked at all times
- Empty fields must show a validation error on submit
- After 3 consecutive failed login attempts the account must be locked
- Locked accounts must display a clear message with next steps

---

## Requirement 2 — Password Reset

**Feature:** Forgot Password Flow  
**Description:** Users who cannot remember their password must be able to 
reset it securely via their registered email address.

**Acceptance Criteria:**
- User clicks "Forgot Password" link on login page
- User enters registered email address
- System sends a password reset link to that email within 2 minutes
- Reset link must expire after 24 hours
- User can set a new password that meets complexity requirements
- After successful reset user is redirected to login page
- Old password must no longer work after reset

---

## Why These Requirements Were Chosen
These two requirements were selected because they represent common, 
real-world features that every QA professional tests. They are complex 
enough to reveal whether AI-generated test cases cover edge cases, 
security scenarios, and failure recovery flows — or only the happy path.
