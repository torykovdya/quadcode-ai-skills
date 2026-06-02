AI Campaign Studio
---
alias: design_create_campaign
description: Transform a brand or product brief into a complete visual campaign — concept, brand system, style anchor, and production-ready marketing assets.
type: tools: designer
subtype: image
tags: campaign, branding, visual, storytelling, image-generation
author: lumi
---

## Purpose

Transform a brand or product brief into a complete visual identity and launch asset system.
Generate a consistent visual language and production-ready assets for social media, websites, presentations, and advertising.

---

## Use When

- Launching a new brand or product
- Needing a visual campaign concept fast
- Exploring creative directions before production
- Creating visual assets for marketing or pitch

---

## Do Not Use When

- User needs a single illustration or icon
- Brief has no product, brand, or audience defined
- User asks for realistic photography of real people

---

## Inputs

- Brand or product description
- Target audience
- Campaign goal (awareness, launch, emotion, conversion)
- Tone (bold, minimal, playful, premium, rebellious, warm)
- Optional: color preferences, visual references

---

## Rules

1. Always define Creative Concept before generating any images
2. Color palette must be established in Step 2 — never change it after
3. All campaign assets must share the same visual identity, color palette, lighting style, and brand personality
4. Each image must serve a different narrative purpose
5. Use Nanobanana for all image generation
6. Prompts must include: mood, lighting, composition, color palette, atmosphere
7. Style Consistency Check is mandatory — never skip it
8. Define a Style Anchor in Step 2 — copy it verbatim into every image prompt
9. At least 70% of generated assets must visualize actual services or outcomes. No more than 30% may use abstract AI symbolism
10. Do not change artistic medium between images (e.g., illustration → photography is prohibited)

---

## Workflow

### Step 1 — Brand Analysis

Extract from brief:
- Brand personality (3 adjectives)
- Target audience (who they are, what they value)
- Campaign goal (what should the audience feel or do)
- Emotional tone (how the campaign should feel)
- Key visual metaphors (what imagery represents this brand)

---

### Step 1.5 — Differentiation Strategy

Analyze:
- Common visual clichés in the category
- Overused color palettes
- Overused imagery and metaphors

Output:
- What competitors typically do
- What this campaign should avoid
- Unique visual territory to own

---

### Step 1.6 — Business Visualization Strategy

Translate services into visuals. For each core service define:
- Visual representation
- Metaphor
- Recurring symbol

Examples:
- Social Media → content streams
- Automation → synchronized gears
- Research → intelligence radar
- Video → media frames

---

### Step 2 — Creative Direction

Define the campaign's visual language:
- Campaign concept (1–2 sentences, the big idea)
- Campaign narrative (the story the images tell together)
- Color palette (4–5 hex codes with names)
- Lighting style (soft/dramatic/natural/studio/cinematic)
- Composition style (minimal/dynamic/macro/wide/abstract)

### Style Anchor

Output a reusable style block containing:
- Artistic style
- Rendering style
- Color palette
- Lighting style
- Aspect ratio
- Quality keywords

This exact block must be copied verbatim into every image prompt.

---

### Step 2.5 — Brand System

Define:
- Visual Identity summary
- Typography Direction
- Iconography Style
- Brand Voice

---

### Step 3 — Asset Planning

Generate a complete launch asset set.

Required assets:
1. Profile Avatar (Founder or Brand Symbol — explain choice)
2. Banner / Cover Image
3. Website Hero Image
4. Social Media Post #1 — Announcement
5. Social Media Post #2 — Product/Service highlight
6. Social Media Post #3 — Customer outcome

For each asset define:
- Marketing Purpose
- Target Platform
- Dimensions
- Visual Objective
- Scene description
- Emotion triggered
- Camera angle and composition

Visual Continuity: at least one recurring visual element must appear across all assets (same character, product, symbol, or environment).

Asset Mapping: map every asset to a specific business use case.

CRITICAL: Profile Avatar and Banner are mandatory. Do not replace them with other assets.

---

### Step 4 — Asset Generation

For every asset output:
- Asset Name
- Purpose
- Target Platform
- Dimensions
- Full prompt (including verbatim Style Anchor)

Generate all assets using Nanobanana model.

---

### Step 5 — Style Consistency Audit

After all assets are generated, verify:

For each category provide Status (PASS / FAIL) and Score (0–100):
- Color Palette
- Lighting Style
- Artistic Style
- Visual Continuity
- Aspect Ratio
- Prompt Consistency

Provide an Overall Consistency Score.

If any category FAILS: flag it and suggest specific prompt adjustment.

---

## Validation

Before final output verify:
- [ ] Creative concept defined before any generation
- [ ] Color palette established in Step 2 and used in all prompts
- [ ] Style Anchor defined and copied verbatim into all prompts
- [ ] All required assets generated (Avatar, Banner, Hero, 3 Social Posts)
- [ ] Each asset serves a distinct marketing purpose
- [ ] Asset Mapping completed
- [ ] Social posts communicate different messages (Announcement / Product / Outcome)
- [ ] Style Consistency Audit completed with scores

---

## Output

A complete launch asset package:

- **Campaign Concept** (the big idea)
- **Campaign Narrative** (the story)
- **Differentiation Strategy** (what to avoid and own)
- **Color Palette** (hex codes with names)
- **Style Anchor** (reusable prompt block)
- **Brand System** summary
- **Asset Mapping** (every asset → business objective)
- **6 Generated Assets** with individual prompts
- **Style Consistency Report** with overall score
