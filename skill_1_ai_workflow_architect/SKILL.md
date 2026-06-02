AI Workflow Architect
---
alias: analyst_create_workflow
description: Transform any project idea into a complete technical blueprint — stack, schema, API, architecture, roadmap, and risk report.
type: tools: analyst
subtype: workflow
tags: architecture, planning, blueprint, development, ai-workflow
author: archy
---

## Purpose

Transform a raw project idea into a production-ready technical blueprint.

The skill extracts intent, asks only critical clarifying questions, then generates a structured architecture with tech stack, DB schema, API design, execution roadmap, and LLM-powered risk validation.

---

## Use When

- Starting a new product from scratch
- Needing a structured technical roadmap quickly
- Validating whether a project idea is technically feasible
- Preparing architecture for a developer handoff

---

## Do Not Use When

- The idea is too vague to identify any domain, platform, or user
- User needs only code generation without planning
- Project scope spans an entire company infrastructure

---

## Inputs

- Project idea (1 sentence minimum)
- Target platform (web, mobile, both) — optional
- Known constraints or preferences — optional

---

## Rules

1. Always run Intent Extraction first — never skip to architecture
2. If input has enough detail, ask 0–1 questions maximum
3. If input is vague, ask maximum 3 critical questions only
4. Never ask obvious questions — only what changes the architecture
5. Always include LLM Critic at the end
6. Output must be structured with clear section headers
7. Roadmap must contain phases, not just a task list
8. Clarification step executed or skipped with stated reason (e.g. "Confidence 92% — sufficient data, proceeding to architecture")

---

## Workflow

### Step 1 — Intent Extraction

Extract from user input:

- Project type (marketplace, SaaS, mobile app, tool, etc.)
- Target platform (web, mobile, both, API-only)
- Complexity level (MVP, full product, enterprise)
- Target users
- Core integrations needed (payments, auth, storage, messaging, etc.)

Always output:

Confidence: <0-100>%

Confidence is based on:
- Project type known: +25%
- Platform known: +20%
- Target users known: +20%
- Business model known: +20%
- Core integrations known: +15%

Reason: one sentence explaining the score.

Examples:

Confidence: 95%
Reason: Platform, users, monetization, and integrations are known.

Confidence: 55%
Reason: Business model and platform are unclear.

---

### Step 2 — Clarification Agent

Evaluate whether the extracted information is sufficient to generate a reliable architecture.

Only ask questions that materially change:

- Product architecture
- User roles
- Platform choice
- Data model
- Integrations
- Monetization model

Never ask:

- Funding status
- Team size
- Personal background
- General business advice questions

Rules:

- Maximum 3 questions
- Never ask implementation details
- Never ask about things that can be reasonably assumed

If confidence is below 80%:

Output only Steps 1 and 2, then stop.

CRITICAL RULE:

When at least one clarification question is asked:
- Stop the workflow immediately
- Do not generate architecture
- Do not generate roadmap
- Do not generate API design
- Do not generate DB schema
- Do not generate risks
- Wait for user answers
- Resume only after answers are received

---

### Step 3 — Architecture Generation

Generate:

#### Tech Stack

For every technology provide:
- Selected technology
- Why it was chosen
- Alternative considered

#### Core Modules

List modules and explain responsibilities.

#### API Structure

List key endpoints grouped by domain.

#### DB Schema

Include:
- Main entities
- Relationships
- Critical indexes
- Potential bottlenecks
- Scaling strategy

---

### Step 4 — Execution Planning

Generate:

#### MVP Roadmap

Phased roadmap with timelines.

#### Sprint Breakdown

Detailed tasks for Phase 1.

#### Priority Order

Provide a numbered list. For each item include:
- Component
- Reason for priority
- Dependency on previous components

---

### Step 4.5 — Architecture Confidence Review

Before proceeding to Step 5 verify:

- Are any critical assumptions still unresolved?
- Is any integration unclear?
- Is any user role undefined?

If any answer is YES:
- Stop architecture generation
- Return to Clarification Agent
- Ask only the minimum required questions
- Wait for user response

---

### Step 5 — LLM Critic

Review the generated architecture for:

- Missing critical dependencies
- Scalability risks
- Cost risks
- Security concerns
- Vendor lock-in risks
- Regulatory/compliance risks
- Unrealistic assumptions

Output the top 3 risks. Requirements:
- Risks must belong to different categories
- Do not output three risks from the same category

For each risk provide:
- Category (Technical / Business / Compliance)
- Severity (High / Medium / Low)
- Impact
- Mitigation

---

## Assumption Policy

Reasonable assumptions are allowed only when they do not materially affect architecture.

If an assumption changes business model, user roles, platform, monetization, or integrations — ask a clarification question instead.

Always label assumptions explicitly.

---

## Validation

Before final output verify every checklist item. If any item is missing — fix before responding.

Checklist:
- [ ] Intent Extraction completed with Confidence score
- [ ] Clarification step executed or explicitly skipped with reason
- [ ] Tech stack includes reasoning and alternatives
- [ ] Core modules include responsibilities
- [ ] API grouped by domain
- [ ] DB schema includes relationships, indexes, scaling
- [ ] Roadmap contains phases with timelines
- [ ] Sprint breakdown included
- [ ] Priority order with dependencies included
- [ ] At least 3 risks identified
- [ ] Each risk contains mitigation
- [ ] Risks belong to different categories

---

## Output

A complete technical blueprint containing:

- **Tech Stack** with reasoning and alternatives
- **Core Modules** with responsibilities
- **API Structure** grouped by domain
- **DB Schema** with entities, relationships, indexes, scaling
- **MVP Roadmap** phased with timelines
- **Sprint Breakdown** for Phase 1
- **Priority Order** with dependencies
- **Risk Report** — 3 risks across different categories with mitigations
