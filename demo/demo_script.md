[demo_script.md](https://github.com/user-attachments/files/28444592/demo_script.md)

# Demo Script — Quadcode AI Skills

**Duration:** 2–3 minutes  
**Format:** Screen recording with voiceover  
**Platform:** Quadcode.ai

---

## Structure

```
0:00–0:25  Problem
0:25–1:20  Skill 1 Demo — AI Workflow Architect
1:20–2:10  Skill 2 Demo — AI Campaign Studio
2:10–2:40  What I learned + what's next
```

---

## Script

### 0:00–0:25 — The Problem

"Two things slow down every product team.

First: starting a new project. You have an idea — but before you can build anything, you need architecture decisions, tech stack choices, database design, a roadmap. That takes hours.

Second: launching anything. You need a visual campaign — brand concept, color palette, marketing assets. That takes days.

These two skills solve both problems on Quadcode.ai."

---

### 0:25–1:20 — Skill 1: AI Workflow Architect

[Show Skills catalog, locate analyst_create_workflow]

"The first skill is AI Workflow Architect. You give it a project idea — any idea — and it produces a complete technical blueprint."

[Type in chat: Use web template with alias: "analyst_create_workflow"]

[Give input: "Freelance marketplace for designers — web and mobile, branding and logo niche, subscription model $5–$50"]

"Watch what happens. The skill first extracts intent from the input — project type, platform, users, integrations — and scores its own confidence. Here it's at 70%, which means it needs two clarifications before proceeding."

[Show clarification questions appearing]

"It asks only the critical questions. Not team size, not budget — only what materially changes the architecture."

[Answer the questions]

"Now it builds. Tech stack with reasoning and alternatives considered. Core modules. API routes grouped by domain. Database schema with indexes and scaling strategy. MVP roadmap with sprint breakdown. And finally — an LLM Critic that finds risks across Technical, Business, and Compliance categories."

[Show the full output scrolling]

"This took about 90 seconds. The same output manually takes hours."

---

### 1:20–2:10 — Skill 2: AI Campaign Studio

[Navigate to new chat]

"The second skill is AI Campaign Studio. You describe a brand — and it builds a complete visual campaign system."

[Type: Use web template with alias: "design_create_campaign"]

[Give input: "Minimalist coffee brand for young professionals. Tone: calm, premium, natural."]

"The skill starts by analyzing what every coffee brand already does — and what to avoid. Then it builds a creative concept, defines the color palette, and creates a Style Anchor — a fixed parameter block that gets copied into every image prompt to prevent style drift."

[Show the Style Anchor block]

"Then it plans 6 assets: profile avatar, banner, website hero, and three social posts — each mapped to a specific marketing purpose."

[Show generated images]

"All three images share the same palette, the same lighting, the same calm editorial feel. That's the Style Anchor working."

---

### 2:10–2:40 — What I Learned

"A few things I discovered while building these.

The hardest part isn't writing the skill — it's anticipating where the agent will fail. The CRITICAL RULE in Skill 1 exists because without it, agents generate architecture before they have enough information. The Style Anchor in Skill 2 exists because without it, images drift by the third generation.

Both skills went through multiple iterations. The iteration notes, edge cases, and evaluation criteria in this repository document exactly what broke and how I fixed it.

The skills are live on Quadcode.ai and available in the project catalog."

---

## Recording Notes

- Record at 1920×1080, 30fps
- Use Quadcode.ai dark theme
- Zoom in on key outputs — text must be readable
- Keep cursor movements deliberate, not rushed
- Voiceover recorded separately and synced in post
- No background music — keep it clean and focused
