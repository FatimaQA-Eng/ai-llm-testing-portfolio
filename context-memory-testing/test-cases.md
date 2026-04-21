# Context & Memory Testing — AI & LLM Portfolio

**Tester:** Fatima Alfred  
**AI Tool Tested:** ChatGPT (GPT-4)  
**Date:** April 2026  
**Goal:** Verify that AI correctly retains and applies information shared earlier in a conversation, and handles context switches without losing track

---

## Test Case CM-001
**Scenario:** User shares personal detail early, checks if AI remembers later  
**Input Step 1:** "My name is Sarah and I am a nurse working in pediatrics."  
**Input Step 2:** (10 messages later) "What career advice would you give me?"  
**Expected Behavior:** AI references nursing/pediatrics context in its advice  
**Actual Behavior:** AI correctly remembered the role and gave pediatric nursing-specific career advice  
**Result:** ✅ PASS  
**Notes:** AI retained user context within the same conversation window

---

## Test Case CM-002
**Scenario:** User corrects themselves mid-conversation — does AI update?  
**Input Step 1:** "I need help planning a vegetarian meal."  
**Input Step 2:** (5 messages later) "Actually I eat chicken, just not red meat."  
**Input Step 3:** "Can you suggest a dinner recipe?"  
**Expected Behavior:** AI uses updated preference (chicken allowed) not original (vegetarian)  
**Actual Behavior:** AI correctly used the updated preference and suggested a chicken-based meal  
**Result:** ✅ PASS  
**Notes:** AI successfully updated its understanding based on user correction

---

## Test Case CM-003
**Scenario:** Testing if AI contradicts itself across a long conversation  
**Input Step 1:** "Is coffee good or bad for health?"  
**AI Response:** Listed both benefits and risks, leaning slightly positive  
**Input Step 2:** (15 messages later) "So overall would you say coffee is harmful?"  
**Expected Behavior:** AI should stay consistent with earlier response  
**Actual Behavior:** AI remained consistent and referenced its earlier balanced answer  
**Result:** ✅ PASS  
**Notes:** No self-contradiction detected within the session

---

## Test Case CM-004
**Scenario:** Context window limit — does AI forget early details in a very long conversation?  
**Input Step 1:** "Remember this code: BLUE42. I will ask you about it later."  
**Input Step 2:** (30+ messages of unrelated conversation later) "What was the code I gave you?"  
**Expected Behavior:** AI recalls BLUE42  
**Actual Behavior:** AI could not recall the code — stated it does not have memory of earlier parts of very long conversations  
**Result:** ❌ FAIL  
**Notes:** This is a known context window limitation. Important finding — AI should ideally warn users upfront that it may not retain details across very long sessions. This is a UX and transparency gap.

---

## Test Case CM-005
**Scenario:** Topic switch — does AI mix up contexts?  
**Input Step 1:** Discussed a Python coding problem for several messages  
**Input Step 2:** Switched topic to meal planning  
**Input Step 3:** Asked a follow-up coding question  
**Expected Behavior:** AI cleanly handles topic switch and returns to coding context correctly  
**Actual Behavior:** AI handled the switch cleanly with no context bleed between topics  
**Result:** ✅ PASS  
**Notes:** Good context management across topic switches within one session

---

## Summary

| Test Case | Scenario | Result |
|-----------|----------|--------|
| CM-001 | Remembering user details | ✅ Pass |
| CM-002 | Updating on user correction | ✅ Pass |
| CM-003 | Self-consistency check | ✅ Pass |
| CM-004 | Context window limit | ❌ Fail |
| CM-005 | Topic switch handling | ✅ Pass |

**Key Finding:** AI performs well at retaining context within normal conversation length. However, CM-004 revealed a real limitation — very early details can be lost in long sessions. This is a known architectural constraint but represents a transparency risk if users assume AI has unlimited memory. A well-designed AI product should proactively warn users about this limitation.
