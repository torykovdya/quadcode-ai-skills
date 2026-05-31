# Edge Cases — AI Campaign Studio

## Case 1: No audience defined

**Input:** "Create a campaign for my new app"

**Expected behavior:**
- Brand Analysis cannot extract target audience
- Skill asks: "Who is this app for — age group, profession, lifestyle?"
- Does not proceed to creative direction without audience definition
- Reason: visual style, tone, and asset format depend entirely on who will see them

---

## Case 2: Contradictory tone

**Input:** "We want something bold and aggressive but also calm and minimal"

**Expected behavior:**
- Differentiation Strategy flags the contradiction
- Skill asks: "Bold and minimal can coexist (think Apple), but bold and calm often conflict — should we prioritize impact or elegance?"
- Proceeds only after tone is resolved
- Reason: Style Anchor cannot be defined with contradictory parameters

---

## Case 3: Request for realistic photography of real people

**Input:** "Generate photos of our CEO presenting at a conference"

**Expected behavior:**
- Triggers Do Not Use When rule
- Responds: "This skill generates AI-illustrated campaign assets, not realistic photography of real people. For this use case, consider professional photography."

---

## Case 4: Single asset request

**Input:** "Just make me a LinkedIn banner"

**Expected behavior:**
- Triggers Do Not Use When rule
- Responds: "This skill generates complete campaign systems (6 assets minimum). For a single asset, use the image generation tools directly."

---

## Case 5: Overcomplicated scene descriptions

**Observed failure:** Early prompts described too many elements in one scene — "a person holding a coffee cup while looking at their phone in a modern kitchen with plants and morning light and a newspaper."

**Result:** Model produced muddy, cluttered compositions with poor hierarchy.

**Fix applied:** Added Rule 6 — prompts must focus on mood, lighting, and atmosphere first. Specific objects are secondary. Prompts reduced to 2–3 focal elements maximum.

---

## Case 6: Style drift between assets

**Observed failure:** Assets 1–3 generated in illustration style, Assets 4–6 drifted toward photorealistic rendering because prompts described different scenes.

**Fix applied:** Style Anchor introduced — identical style block copied verbatim into every prompt. Drift eliminated in subsequent tests.

---

## Case 7: Abstract-only campaign

**Observed failure:** First version of the skill allowed all assets to be abstract visual metaphors. Result: beautiful images that communicated nothing about the brand.

**Fix applied:** 70/30 rule — at least 70% of assets must show concrete business context. Skill now plans asset mix explicitly in Step 3 before generation.
[skill2_edge_cases.md](https://github.com/user-attachments/files/28444678/skill2_edge_cases.md)

