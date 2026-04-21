# Bug Report — Context & Memory Testing
**Tester:** Fatima Alfred  
**AI Tool:** ChatGPT (GPT-4)  
**Date:** April 2026  

---

## BUG-CM-001
**Severity:** High  
**Title:** AI loses early conversation context in long sessions  
**Prompt Used:** "Remember this code: BLUE42. I will ask you about it later." — asked to recall after 30+ messages  
**Expected:** AI recalls BLUE42 when asked later in the same conversation  
**Actual:** AI stated it could not access earlier parts of the conversation and asked user to repeat the information  
**Risk:** Users who share important details early in a conversation may assume AI remembers — leading to errors in high-stakes workflows  
**Status:** Open  
**Note:** This is a known context window limitation but represents a transparency gap — AI should proactively warn users that memory has limits  

---

## Detailed Findings

| Test Case | Scenario | Result |
|-----------|----------|--------|
| CM-001 | Remembering user details mid-conversation | ✅ Pass |
| CM-002 | Updating preference based on user correction | ✅ Pass |
| CM-003 | Self-consistency across long conversation | ✅ Pass |
| CM-004 | Recalling detail after 30+ messages | ❌ Fail |
| CM-005 | Handling topic switches cleanly | ✅ Pass |

---

## Observations & Risks

**Positive Finding:**  
AI handles short to medium length conversations well — remembering user details, updating on corrections, and staying consistent.

**Critical Finding:**  
Context window limitation causes AI to forget early details in very long conversations. This is particularly risky in:
- Customer support workflows
- Medical or legal consultation scenarios  
- Any multi-step process where early context matters

**Recommendation:**  
AI products should display a visible warning when conversations approach context limits, similar to how apps warn about storage or session timeouts.

---

## Summary
| Bug ID | Severity | Status |
|--------|----------|--------|
| BUG-CM-001 | High | Open |

**Overall Finding:** AI memory works well within normal conversation length but fails to retain very early details in long sessions. This is the most significant real-world risk found across all context/memory testing scenarios.
