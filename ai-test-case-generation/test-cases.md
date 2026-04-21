# AI Test Case Generation — AI & LLM Portfolio

**Tester:** Fatima Alfred  
**AI Tool Used:** ChatGPT (GPT-4)  
**Date:** April 2026  
**Goal:** Evaluate how well AI can generate test cases from a sample requirement, 
and compare AI output against manually written test cases

---

## Sample Requirement Used

**Feature:** Login Page for a web application  
**Requirement:** Users must be able to log in using a valid email and password. 
Invalid credentials should show an error message. 
The password field should be masked. 
After 3 failed attempts, the account should be locked.

---

## AI-Generated Test Cases (ChatGPT Output)

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

---

## Manually Written Test Cases (Fatima's QA Analysis)

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
| M-009 | Attempt login after lockout | Clear lockout message + instructions |
| M-010 | Check lockout resets after time period | Access restored after defined window |
| M-011 | SQL injection in email field | No system error — safe rejection |
| M-012 | Very long string in password field | Handled gracefully, no crash |

---

## Comparison Analysis

| Category | AI Generated | Manually Written |
|----------|-------------|-----------------|
| Total test cases | 8 | 12 |
| Happy path | ✅ Covered | ✅ Covered |
| Basic negative cases | ✅ Covered | ✅ Covered |
| Edge cases (spaces, paste) | ❌ Missed | ✅ Covered |
| Security testing (SQL injection) | ❌ Missed | ✅ Covered |
| Post-lockout recovery | ❌ Missed | ✅ Covered |
| Specific redirect behavior | ❌ Missed | ✅ Covered |

---

## Key Findings

**What AI did well:**
- Generated a solid baseline set of test cases quickly
- Covered all the happy path and obvious negative scenarios
- Useful as a starting point to save time

**What AI missed:**
- Edge cases like spaces-only input and copy-paste behavior
- Security scenarios like SQL injection
- Post-lockout recovery flow
- Specific UI behavior details like redirect destination

**Conclusion:**  
AI-generated test cases are a great starting point and can speed up 
test planning significantly. However, they should never replace a 
manual QA review. An experienced QA professional adds critical thinking 
around edge cases, security, and real user behavior that AI consistently 
misses. The best approach is AI + human review together.
