# Design Decisions

Key architectural and prompt engineering decisions made during skill development, with reasoning.

---

## Skill 1 — AI Workflow Architect

### Decision 1: Multi-stage pipeline instead of single prompt

**What:** 5 discrete steps (Intent → Clarification → Architecture → Planning → Critic) instead of one large prompt.

**Why:** A single "generate architecture" prompt produces generic, inconsistent output. Multi-stage forces the agent to build understanding before generating, which dramatically improves output quality and reliability.

**Tradeoff:** More tokens per run, slower execution. Acceptable because the output quality difference is significant.

---

### Decision 2: Confidence scoring in Intent Extraction

**What:** After Step 1, the agent outputs a Confidence score (0–100%) with a breakdown of what is and isn't known.

**Why:** Without a forcing function, agents tend to proceed even with incomplete information. The confidence score makes the decision to ask questions or proceed explicit and auditable.

**How confidence is calculated:**
- Project type known: +25%
- Platform known: +20%
- Target users known: +20%
- Business model known: +20%
- Core integrations known: +15%

---

### Decision 3: CRITICAL RULE — hard stop on clarification

**What:** If any clarification question is asked, the agent stops completely. No architecture, no roadmap, no risks. Waits for user response.

**Why:** Without this rule, agents "helpfully" generate architecture while also asking questions — producing output based on unresolved assumptions. This creates the illusion of completeness while hiding critical unknowns.

**Observed in testing:** Without the CRITICAL RULE, the agent generated a full tech stack for the tutoring app before knowing the target curriculum. The architecture changed significantly after clarification.

---

### Decision 4: Step 4.5 — Architecture Confidence Review

**What:** A checkpoint between Execution Planning and LLM Critic that re-evaluates whether any assumptions are still unresolved.

**Why:** Architecture generation sometimes surfaces new unknowns not visible at intake. This step catches gaps before the LLM Critic runs, preventing the Critic from validating an incomplete architecture.

---

### Decision 5: LLM Critic must span different risk categories

**What:** The Critic must identify risks from different categories (Technical / Business / Compliance), not three technical risks.

**Why:** Without this constraint, the Critic defaults to technical risks only. Real projects fail for business and compliance reasons too. Forcing category diversity produces more useful risk analysis.

---

### Decision 6: Assumption Policy as a separate section

**What:** Explicit policy on when assumptions are allowed vs when clarification is required.

**Why:** Without this, agents over-assume on architectural decisions. The policy defines the boundary: assumptions are only allowed when they don't materially change the architecture.

---

## Skill 2 — AI Campaign Studio

### Decision 1: Style Anchor as a fixed reusable block

**What:** A Style Anchor is defined in Step 2 and copied verbatim into every image prompt.

**Why:** The primary failure mode in multi-image generation is style drift — images drift toward different aesthetics with each generation. The Style Anchor prevents this by making the visual language a fixed artifact, not a re-interpreted description.

---

### Decision 2: Differentiation Strategy before creative direction

**What:** Step 1.5 analyzes category clichés, overused palettes, and visual tropes before defining the creative concept.

**Why:** Without this step, AI-generated campaigns default to generic category aesthetics (e.g., coffee brands getting warm browns and latte art). The Differentiation Strategy forces deliberate distinction.

---

### Decision 3: 70/30 rule — concrete vs abstract imagery

**What:** At least 70% of generated assets must show concrete business context (product, service, outcome, people). Maximum 30% may use abstract visual metaphors.

**Why:** Abstract AI-generated imagery is visually impressive but communicates nothing specific. Real marketing assets need to show what the product does and who it's for.

---

### Decision 4: Asset Mapping to business objectives

**What:** Every generated asset is mapped to a specific marketing purpose (Profile Avatar → Founder profile, Banner → LinkedIn, etc.).

**Why:** Generating images without a defined purpose produces beautiful but unusable assets. Asset Mapping ensures every generation has a specific deployment context.

---

### Decision 5: Style Consistency Report with PASS/FAIL scores

**What:** After generation, a structured audit with scores per category (Color Palette, Lighting, Artistic Style, Visual Continuity, Aspect Ratio, Prompt Consistency).

**Why:** Qualitative consistency checks ("does this look right?") are subjective and unreliable. Structured scoring makes consistency measurable and improvable across iterations.

---

### Decision 6: Nanobanana as the required model

**What:** All image generation explicitly uses Nanobanana.

**Why:** Testing showed Nanobanana produces the most consistent style across multiple generations from the same Style Anchor. Other models showed more variation between runs.
