# Architecture — AI Campaign Studio

## Pipeline Overview

```
User Brief
    ↓
Step 1: Brand Analysis
    ├── Brand personality (3 adjectives)
    ├── Target audience
    ├── Campaign goal
    └── Key visual metaphors
    ↓
Step 1.5: Differentiation Strategy
    ├── Category clichés to avoid
    └── Unique visual territory to own
    ↓
Step 1.6: Business Visualization Strategy
    └── Services → visual metaphors mapping
    ↓
Step 2: Creative Direction
    ├── Campaign concept + narrative
    ├── Color palette (4–5 hex codes)
    ├── Lighting + composition style
    └── Style Anchor (fixed reusable block)
    ↓
Step 2.5: Brand System
    └── Typography, iconography, brand voice
    ↓
Step 3: Asset Planning
    ├── 6 required assets defined
    ├── Each asset mapped to business objective
    └── Visual continuity element identified
    ↓
Step 4: Asset Generation (Nanobanana)
    ├── Asset 1: Profile Avatar
    ├── Asset 2: Banner / Cover
    ├── Asset 3: Website Hero
    ├── Asset 4: Social Post #1 (Announcement)
    ├── Asset 5: Social Post #2 (Product)
    └── Asset 6: Social Post #3 (Outcome)
    ↓
Step 5: Style Consistency Audit
    └── PASS/FAIL per category + Overall Score
    ↓
Final Output: Complete Launch Asset Package
```

---

## The Style Anchor — Core Design Decision

The Style Anchor is the most important architectural element of this skill.

**Problem it solves:** Multi-image generation naturally drifts. Each prompt is interpreted independently by the model, causing the 3rd image to look like a different brand than the 1st.

**How it works:** In Step 2, a fixed style block is defined containing artistic style, rendering style, color palette, lighting, aspect ratio, and quality keywords. This exact block is then copied verbatim — not paraphrased — into every subsequent image prompt.

**Result:** Visual consistency across all 6 assets because the model receives identical style instructions every time.

---

## Differentiation Strategy — Why It Exists

Without Step 1.5, AI-generated campaigns default to category visual tropes:
- Coffee brands → warm browns, latte art, rustic wood
- Tech startups → blue gradients, circuit patterns, floating UI
- Wellness brands → pastel colors, minimalist white space

The Differentiation Strategy forces the skill to analyze what's common before defining what's unique. This produces campaigns that stand out rather than blend in.

---

## 70/30 Rule — Concrete vs Abstract

At least 70% of assets must show concrete business context (product, service, people, outcomes). Maximum 30% may use abstract visual metaphors.

**Why:** Abstract AI imagery is visually impressive but communicates nothing specific. A campaign of 6 abstract images looks beautiful in isolation but fails as marketing because viewers don't understand what the brand does.

---

## Asset Sequence Logic

The 6 required assets follow a deliberate marketing narrative:

| Asset | Purpose | Narrative Role |
|-------|---------|----------------|
| Profile Avatar | Identity anchor | Who we are |
| Banner | First impression | What we stand for |
| Website Hero | Conversion page | Why choose us |
| Social Post 1 | Announcement | We exist |
| Social Post 2 | Product | What we do |
| Social Post 3 | Outcome | What you get |

---

## Style Consistency Audit — Why It's Scored

Qualitative consistency checks ("does this look right?") are subjective and unreliable across different reviewers and sessions.

Structured scoring per category makes consistency:
- Measurable across iterations
- Comparable between different campaign runs
- Actionable — a FAIL on Color Palette tells you exactly what to fix
[skill2_architecture.md](https://github.com/user-attachments/files/28444674/skill2_architecture.md)

