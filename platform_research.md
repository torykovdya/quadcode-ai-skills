# Platform Research — Quadcode.ai

Observations made during hands-on exploration of the Quadcode.ai platform before and during skill development.

---

## Platform Architecture

Quadcode.ai is an AI-native IDE where agents execute tasks on behalf of users. The platform combines:

- **Multi-agent system** with specialized agents (Archy, Lumi, Cody, Sonic, etc.)
- **Skill catalog** — reusable templates loadable by alias
- **Multimodal generation** — image, video, audio via dedicated model nodes
- **Project file system** — skills live in `skills/<alias>/SKILL.md`
- **Cluster infrastructure** — LLM nodes and media nodes run separately

---

## How Skills Work

Skills are Markdown files with YAML frontmatter. They are:

1. Stored in `skills/<alias>/SKILL.md` inside the project
2. Auto-detected and loaded into the template catalog on startup
3. Invoked by agents via `ToolGetTemplateContent` using the alias
4. Executed by whatever agent is active when the skill is called

**Key insight:** The skill file IS the prompt. There is no separate prompt configuration. Everything the agent knows about how to execute the skill comes from the SKILL.md body.

---

## Agent Specialization

| Agent | Role | Best for |
|-------|------|---------|
| Archy | Senior Developer | Creating files, build mode operations |
| Lumi | Designer | Image generation, visual tasks |
| Cody | Developer | Code tasks, exploration |
| Sonic | Motion Designer | Video and animation |
| Sage | Business Analyst | Analysis and research |

**Important discovery:** Agents operate in two modes:
- **Exploration Mode** — reads and plans, cannot execute file creation or generation
- **Build Mode** (Ctrl+Shift+Enter) — executes actions, creates files, triggers generation

Skills requiring file creation or image generation must be run in Build Mode.

---

## Image Generation

Available image models observed:
- **Nanobanana** — highest quality, best for reference-based generation (~9.2 qcc/image)
- **GPT-Image** — best for UI/diagrams (~4.2 qcc/image)
- **Flux 2 Pro** — strong with image references (~1.8 qcc/image)
- **Grok Image** — fast, good quality (~1.2 qcc/image)
- **Luma Image** — optional references (~0.51 qcc/image)

**Design choice:** Nanobanana selected for AI Campaign Studio due to highest output quality and reference consistency.

---

## Skill Loading Behavior

- Skills are loaded from `skills/` folder automatically
- Folder name must exactly match the `alias` field in frontmatter
- Changes to SKILL.md are picked up on next catalog refresh
- User skills appear alongside API templates in the catalog

---

## Platform Strengths

- Fast skill iteration cycle — edit SKILL.md, test immediately
- Agent switching allows using the right tool for each task
- Multimodal generation integrated into the same workflow
- Rich model selection for different quality/cost tradeoffs

## Platform Constraints Observed

- Agents default to Exploration Mode — Build Mode must be triggered explicitly
- Image generation requires Lumi agent or direct model invocation
- File creation by agents requires explicit permission grants
- Skills are project-local — not shared across projects by default
