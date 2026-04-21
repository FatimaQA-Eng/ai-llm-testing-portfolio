# Manual vs AI-Generated Test Cases — Comparison
**Tester:** Fatima Alfred  
**AI Tool:** ChatGPT (GPT-4)  
**Date:** April 2026  
**Purpose:** Compare AI-generated test cases against manually written ones 
to identify gaps, strengths, and limitations of using AI in test planning

---

## Requirement 1 — Login Page

### AI-Generated Test Cases
| TC ID | Test Case | Expected Result |
|-------|-----------|----------------|
| AI-001 | Enter valid email and valid password | User logs in successfully |
| AI-002 | Enter valid email and wrong password | Error message displayed |
| AI-003 | Enter invalid email format | Error message displayed |
| AI-004 | Leave email field empty | Validation error shown |
| AI-005 | Leave password field empty | Validation error shown |
| AI-006 | Verify password field is masked | Password characters show as dots |
| AI-007 | Enter wrong credentials 3 times | Account locked message displayed |
| AI-008 | Try to login after account is locked | Access denied message shown |

### Manually Written Test Cases
| TC ID | Test Case | Expected Result |
|-------|-----------|----------------|
| M-001 | Enter valid email and valid password | User logs in, redirected to dashboard |
| M-002 | Enter valid email and wrong password | "Invalid credentials" error shown |
| M-003 | Enter invalid email format (missing @) | Inline validation error on email field |
| M-004 | Leave both fields empty and click Login | Both fields show required error |
| M-005 | Enter spaces only in email field | Treated as empty — validation error |
| M-006 | Verify password field masking on entry | Characters masked immediately on type |
| M-007 | Copy-paste password — verify masking | Pasted text also masked |
| M-008 | Enter wrong credentials exactly 3 times | Account locked after 3rd attempt |
| M-009 | Attempt login after lockout | Clear lockout message + next steps |
| M-010 | Check lockout resets after time period | Access restored after defined window |
| M-011 | SQL injection in email field | No system error — safe rejection |
| M-012 | Very long string in password field | Handled gracefully, no crash |

---

## Requirement 2 — Password Reset

### AI-Generated Test Cases
| TC ID | Test Case | Expected Result |
|-------|-----------|----------------|
| AI-009 | Click Forgot Password link | Redirected to password reset page |
| AI-010 | Enter registered email and submit | Reset email sent confirmation shown |
| AI-011 | Enter unregistered email | Error or generic confirmation shown |
| AI-012 | Use reset link within 24 hours | User can set new password |
| AI-013 | Use reset link after 24 hours | Link expired message shown |

### Manually Written Test Cases
| TC ID | Test Case | Expected Result |
|-------|-----------|----------------|
| M-013 | Click Forgot Password link | Redirected to reset page |
| M-014 | Enter registered email and submit | Reset email received within 2 minutes |
| M-015 | Enter unregistered email | Generic message shown — no account enumeration |
| M-016 | Use reset link within 24 hours | New password can be set successfully |
| M-017 | Use reset link after 24 hours | Clear expiry message with option to resend |
| M-018 | Use same reset link twice | Second use rejected — link invalidated |
| M-019 | New password same as old password | System rejects — must be different |
| M-020 | New password below complexity requirement | Inline validation error shown |
| M-021 | Verify old password no longer works after reset | Login with old password fails |
| M-022 | Verify redirect to login page after reset | User lands on login page with success message |

---

## Gap Analysis

| Coverage Area | AI Generated | Manual |
|--------------|-------------|--------|
| Happy path | ✅ Covered | ✅ Covered |
| Basic negative cases | ✅ Covered | ✅ Covered |
| Edge cases (spaces, paste, long strings) | ❌ Missed | ✅ Covered |
| Security (SQL injection, account enumeration) | ❌ Missed | ✅ Covered |
| Post-lockout recovery | ❌ Missed | ✅ Covered |
| Link invalidation after use | ❌ Missed | ✅ Covered |
| Password complexity validation | ❌ Missed | ✅ Covered |
| Redirect behavior | ❌ Missed | ✅ Covered |

---

## Key Findings

**What AI did well:**
- Generated a solid happy path baseline quickly
- Covered obvious positive and negative scenarios
- Useful as a first draft to save time

**What AI consistently missed:**
- Security scenarios like SQL injection and account enumeration
- Edge cases like spaces-only input and copy-paste behavior
- Post-failure recovery flows
- Specific UI behavior like redirect destinations
- Boundary conditions like password complexity rules

**Conclusion:**
AI-generated test cases are a valuable starting point and can speed up 
test planning by 30-40%. However they should never replace a manual QA 
review. An experienced QA professional adds critical thinking around 
security, edge cases, and real user behavior that AI consistently misses. 
The ideal workflow is AI generates the first draft — QA engineer reviews, 
fills gaps, and adds domain knowledge on top.
