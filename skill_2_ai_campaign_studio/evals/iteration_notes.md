# Iteration Notes — AI Campaign Studio

## v1 — Initial Build

**What was built:**
Basic skill generating 3 moodboard images with consistent color palette and mood.

**Problems observed:**

1. Style drift — Image 3 looked noticeably different from Image 1 despite same brief
2. Abstract imagery dominated — beautiful but not communicating what the brand does
3. No differentiation step — output defaulted to category visual tropes (coffee → warm brown, latte art)
4. Only 3 images — insufficient for a real launch asset system

---

## v1 → v2 Fixes

**Fix 1: Style Anchor introduced**
Added a fixed reusable style block in Step 2. Required it to be copied verbatim into every prompt.

Result: Style drift eliminated. All images now share identical style parameters.

**Fix 2: 70/30 rule added**
Added explicit constraint — at least 70% of assets must show concrete business context. Maximum 30% abstract.

Result: Campaign output became more functional and communicative, not just visually impressive.

**Fix 3: Differentiation Strategy added (Step 1.5)**
Added category cliché analysis before creative direction is defined.

Result: Coffee brand campaign avoided warm browns and latte art entirely, owned muted sage + paper white territory instead.

---

## v2 — Test Results

**Test 1: Minimalist coffee brand for young professionals**
- Input quality: medium (tone and audience clear, no color preferences)
- Differentiation: correctly identified latte art and warm brown as clichés to avoid
- Style Anchor: defined and applied consistently across 3 generated images
- Images generated: 3 (lifestyle, product macro, abstract texture)
- Style Consistency Score: 93.5
- Status: ✅ Pass

**Observed issue:** Only 3 images were generated — skill scope was too narrow for a real launch campaign.

---

## v2 → v3 Fixes (current version)

**Fix 4: Asset system expanded to 6 required assets**
Added Profile Avatar, Banner, Website Hero alongside 3 Social Posts. Each asset mapped to a specific marketing objective.

**Fix 5: Asset Mapping added**
Every asset is now connected to a business use case before generation begins.

**Fix 6: Brand System section added (Step 2.5)**
Added typography direction, iconography style, and brand voice to give the campaign system full identity coverage beyond images.

**Fix 7: Visual Continuity requirement added**
At least one recurring visual element must appear across all assets. Prevents the campaign from feeling like 6 unrelated images.

**Fix 8: Style Consistency Audit formalized**
Replaced qualitative check ("does this look right?") with structured PASS/FAIL scoring per category.

---

## Known Limitations

- Skill generates prompts for all 6 assets but image generation is triggered manually per asset
- Style Anchor consistency depends on the agent correctly copying the block verbatim — occasional paraphrasing observed
- Abstract Asset 6 (texture/mood) sometimes scores lower on Visual Continuity because it doesn't show the product directly — this is acceptable within the 70/30 rule
- Nanobanana is specified but agents may default to a different model if not reminded
[skill2_iteration_notes.md](https://github.com/user-attachments/files/28444681/skill2_iteration_notes.md)

