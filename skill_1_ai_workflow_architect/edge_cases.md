# Edge Cases — AI Workflow Architect

## Case 1: Extremely vague input

**Input:** "I want to build an app"

**Expected behavior:**
- Confidence score: ~20%
- Clarification Agent asks 3 questions:
  1. What does the app do? Who uses it?
  2. What platform — web, mobile, or both?
  3. Is there any monetization or key integration needed?
- Workflow stops. No architecture generated.

**Risk if not handled:** Agent generates a generic "React + Node + PostgreSQL" stack that fits nothing and impresses no one.

---

## Case 2: Over-specified input

**Input:** Full product specification with tech preferences, team size, budget, timeline, existing codebase details.

**Expected behavior:**
- Confidence score: 95–100%
- Clarification Agent: 0 questions asked, proceeds directly
- Architecture generated immediately, tailored to stated constraints

---

## Case 3: Contradictory requirements

**Input:** "Build a real-time collaborative tool that works fully offline"

**Expected behavior:**
- Clarification Agent flags the contradiction
- Asks: "Real-time collaboration requires connectivity — should offline mode support read-only access, or do you need full offline sync with conflict resolution?"
- Does not generate architecture until resolved

---

## Case 4: Scope too large

**Input:** "Build the entire infrastructure for a Fortune 500 company"

**Expected behavior:**
- Skill triggers Do Not Use When rule
- Responds: "This scope exceeds what this skill is designed for. Please scope to a single product or service."
- Does not proceed to architecture

---

## Case 5: Request for code, not architecture

**Input:** "Write me the login component in React"

**Expected behavior:**
- Skill triggers Do Not Use When rule
- Responds: "This skill generates technical blueprints and architecture, not code. For code generation, use a development agent directly."

---

## Case 6: Missing business model

**Input:** "Social network for pet owners, mobile app, iOS and Android"

**Expected behavior:**
- Confidence score: ~65% (platform known, users known, business model unknown)
- Clarification Agent asks: "What's the monetization model — subscription, freemium, ads, or marketplace?"
- This question materially affects infrastructure choices (payment integration, ad serving, etc.)

---

## Case 7: Conflicting platform preferences

**Input:** "Web app but also needs to work as a native iOS and Android app with offline support"

**Expected behavior:**
- Clarification Agent asks: "Do you need truly native iOS/Android apps, or is a Progressive Web App (PWA) acceptable? This significantly affects the tech stack."
- Stops until answered — React Native vs PWA is a fundamental architectural decision
