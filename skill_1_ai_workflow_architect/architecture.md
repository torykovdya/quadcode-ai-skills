# Architecture — AI Workflow Architect

## Pipeline Overview

```
User Input
    ↓
Step 1: Intent Extraction
    ↓
Confidence Score (0–100%)
    ↓
Step 2: Clarification Agent
    ├── Confidence ≥ 80% → proceed
    └── Confidence < 80% → ask ≤3 questions → STOP → wait for answers
    ↓
Step 3: Architecture Generation
    ├── Tech Stack (with reasoning + alternatives)
    ├── Core Modules
    ├── API Structure
    └── DB Schema (entities, indexes, scaling)
    ↓
Step 4: Execution Planning
    ├── MVP Roadmap (phases)
    ├── Sprint Breakdown (Phase 1 detail)
    └── Priority Order (with dependencies)
    ↓
Step 4.5: Architecture Confidence Review
    └── Unresolved assumptions? → return to Clarification
    ↓
Step 5: LLM Critic
    └── Top 3 risks (different categories) with mitigation
    ↓
Final Output: Complete Technical Blueprint
```

---

## Why This Sequence

**Intent before architecture** — generating architecture without understanding the project produces generic output that fits every project and none specifically.

**Confidence scoring before clarification** — makes the decision to ask questions explicit. The agent doesn't guess whether it has enough information — it calculates.

**Hard stop on clarification** — prevents the agent from generating premature architecture based on unresolved assumptions. This is the most common failure mode in workflow skills.

**Step 4.5 before LLM Critic** — catching gaps after architecture generation (not before) allows the agent to surface unknowns that only become visible once the architecture is laid out.

**LLM Critic last** — validates the complete output, not intermediate steps. Risk analysis is only meaningful when there is something complete to analyze.

---

## Hallucination Reduction Strategy

- **Confidence scoring** forces explicit uncertainty acknowledgment
- **Assumption Policy** limits what can be assumed without user input
- **Validation Checklist** before final output catches missing sections
- **CRITICAL RULE** prevents generation under uncertainty
- **LLM Critic** provides adversarial review of generated content

---

## Output Structure

Every run produces the same structured output regardless of input:

| Section | Required | Notes |
|---------|----------|-------|
| Tech Stack | Yes | Must include reasoning and alternatives |
| Core Modules | Yes | With responsibilities |
| API Structure | Yes | Grouped by domain |
| DB Schema | Yes | Entities, relationships, indexes, scaling |
| MVP Roadmap | Yes | Phased with timelines |
| Sprint Breakdown | Yes | Phase 1 in detail |
| Priority Order | Yes | Numbered with dependencies |
| Risk Report | Yes | 3 risks, different categories |

---

## Adaptive Behavior

The skill adapts to input quality:

| Input Quality | Clarification Questions | Behavior |
|--------------|------------------------|---------|
| High (≥80% confidence) | 0–1 | Proceeds directly to architecture |
| Medium (60–79%) | 1–2 | Asks only blocking questions |
| Low (<60%) | 2–3 | Asks all critical questions, stops |

This was observed and confirmed during testing (see iteration_notes.md).
