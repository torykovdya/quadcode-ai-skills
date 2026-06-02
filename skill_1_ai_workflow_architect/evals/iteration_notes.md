## v1 — Initial Build

**What was built:**
Basic 5-step pipeline with intent extraction, clarification, architecture, roadmap, and LLM critic.

**Problems observed:**

1. Agent generated architecture while also asking clarification questions — output was based on unresolved assumptions
2. LLM Critic produced three technical risks every time, never surfacing business or compliance risks
3. No measurable signal for when to ask questions vs proceed — agent behavior was inconsistent

---

## v1 → v2 Fixes

**Fix 1: CRITICAL RULE added to Step 2**
Added explicit instruction: when any clarification question is asked, stop immediately. Do not generate architecture, roadmap, API, schema, or risks. Wait for user answers.

Result: Agent now correctly stops mid-workflow when clarification is needed.

**Fix 2: LLM Critic category requirement**
Added rule: risks must belong to different categories (Technical / Business / Compliance). Three risks from the same category is a validation failure.

Result: Risk reports now consistently surface cross-domain risks.

**Fix 3: Confidence scoring introduced**
Added 0–100% confidence system in Step 1 with explicit breakdown (project type +25%, platform +20%, etc.). Threshold set at 80% for automatic proceed.

Result: Clarification decisions became predictable and consistent.

---

## v2 — Test Results

**Test 1: AI-powered tutoring app for math learners**
- Input quality: low (vague, 1 sentence)
- Confidence score: 60%
- Questions asked: 3 (math level, interaction style, offline requirements)
- Workflow: correctly stopped, resumed after answers
- Output quality: complete blueprint with FERPA compliance risk identified
- Status: ✅ Pass

**Test 2: Freelance marketplace for designers**
- Input quality: medium-high (platform stated, users stated, no monetization)
- Confidence score: 70%
- Questions asked: 2 (not 3 — sufficient data for most decisions)
- Workflow: adaptive behavior confirmed — fewer questions on better input
- Output quality: full blueprint including KYC/AML compliance risk
- Status: ✅ Pass

---

## Key Finding

**Adaptive clarification works as designed.**
The agent correctly scales the number of questions to input quality. This was not explicitly programmed as a formula — it emerges from the confidence scoring system and the "only ask what materially changes the architecture" rule.

---

## v2 → v3 Fixes (current version)

**Fix 4: Step 4.5 added — Architecture Confidence Review**
Observed that architecture generation sometimes surfaced new unknowns not visible at intake. Added a checkpoint between Step 4 and Step 5 to catch these before the LLM Critic runs.

**Fix 5: Assumption Policy section added**
Explicit policy defining when assumptions are allowed vs when clarification is required. Prevents agents from over-assuming on architectural decisions.

**Fix 6: Do Not Use When — third condition added**
Added "The idea is too vague to identify any domain, platform, or user" to prevent the skill from attempting to generate architecture for completely undefined inputs.

---

## Known Limitations

- Skill does not handle multi-product architectures (by design — see Do Not Use When)
- Very long user inputs may cause the agent to skip clarification even when beneficial
- LLM Critic quality depends on the underlying model — weaker models produce generic risks
loading iteration_notes.md

