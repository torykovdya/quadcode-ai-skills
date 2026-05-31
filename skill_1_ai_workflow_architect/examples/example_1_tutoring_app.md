# Example 1 — AI-Powered Tutoring App

## Input

"AI-powered tutoring app for math learners"

---

## Step 1 — Intent Extraction

- **Project Type:** Educational SaaS / EdTech
- **Platform:** Web (React/Next.js) + Mobile (React Native)
- **Complexity:** High — requires real-time LLM interaction, math rendering, user progress tracking
- **Target Users:** K-12 students, university students, lifelong learners
- **Integrations:** OpenAI API (GPT-4o for reasoning), MathJax/KaTeX (rendering), Firebase (Auth/DB)

**Confidence: 60%**
Reason: Platform and domain are clear, but curriculum scope, interaction style, and offline requirements are unknown — all of which affect architecture.

---

## Step 2 — Clarification Agent

3 questions asked:

1. **Math Level:** Are we focusing on a specific curriculum (e.g., Common Core, SAT/ACT prep, University Calculus)?
2. **Interaction Style:** Should the app be a chat-based tutor, a step-by-step problem solver, or a gamified learning platform?
3. **Offline/Sync:** Is offline access a requirement, or will it be strictly online-first?

Workflow stopped. Waiting for user answers.

---

## User Answers

"Focus on K-12 (Common Core) + SAT prep, chat-based tutor with step-by-step problem solving, online-first (no full offline, allow limited offline caching)."

---

## Step 3 — Architecture Generation

### Tech Stack

| Layer | Selected | Why | Alternative |
|-------|----------|-----|-------------|
| Frontend Web | Next.js 14 | SSR for SEO, App Router for layouts | Remix |
| Mobile | React Native | Shared logic with web | Flutter |
| Backend | Node.js + Express | Fast API, large AI ecosystem | FastAPI (Python) |
| Database | PostgreSQL | Relational data for progress tracking | MySQL |
| AI | OpenAI GPT-4o | Best math reasoning, function calling | Gemini 1.5 Pro |
| Math Rendering | MathJax | Industry standard for math display | KaTeX |
| Auth | Firebase Auth | Fast setup, social login | Auth0 |
| Cache | Redis | Session and response caching | Memcached |

### Core Modules

- **Auth & Profiles** — student accounts, parent accounts, progress history
- **Tutor Chat Engine** — LLM conversation with math context, step-by-step mode
- **Curriculum Manager** — Common Core + SAT topic mapping
- **Progress Tracker** — scores, weak areas, learning streaks
- **Math Renderer** — inline and block math expression display
- **Offline Cache** — last 10 sessions cached locally

### API Structure

```
POST   /auth/register
POST   /auth/login
GET    /curriculum/topics
POST   /tutor/chat
GET    /tutor/session/:id
GET    /progress/:userId
POST   /progress/update
GET    /problems/:topic
POST   /problems/submit
```

### DB Schema

**Users:** id, email, role (student/parent), grade_level, created_at
**Sessions:** id, user_id, topic, messages (JSONB), score, created_at
**Progress:** id, user_id, topic_id, mastery_score, attempts, last_attempt
**Topics:** id, name, curriculum (common_core/sat), difficulty, parent_topic_id

Indexes: user_id on Sessions and Progress, topic_id on Progress
Scaling: Read replicas for progress queries, Redis cache for active sessions

---

## Step 4 — Execution Planning

### MVP Roadmap

**Phase 1 (Weeks 1–3):** Auth, user profiles, basic chat with GPT-4o
**Phase 2 (Weeks 4–6):** Math rendering, curriculum topic mapping, progress tracking
**Phase 3 (Weeks 7–9):** Mobile app, offline cache, SAT prep mode
**Phase 4 (Weeks 10–12):** Analytics dashboard, parent view, performance optimization

### Priority Order

1. Auth & Profiles — foundation for all user data
2. Tutor Chat Engine — core product value
3. Math Rendering — without this, math is unreadable
4. Progress Tracker — depends on sessions data
5. Curriculum Manager — depends on topics schema
6. Mobile App — depends on stable web API
7. Offline Cache — depends on mobile app

---

## Step 5 — LLM Critic

**Risk 1 — Technical / High**
LLM response latency (2–4s) will feel slow in a chat tutoring context.
Mitigation: Stream responses token-by-token, show typing indicator, cache common problem explanations.

**Risk 2 — Business / Medium**
K-12 apps require COPPA compliance for users under 13 — parental consent flows add significant scope.
Mitigation: Implement parental consent gate at registration, consult legal on data retention rules.

**Risk 3 — Compliance / High**
Student data (progress, messages) is subject to FERPA in the US.
Mitigation: Ensure all data is encrypted at rest, implement data deletion endpoints, document data handling policy.

---

## Outcome

Full pipeline executed. Adaptive behavior confirmed — confidence was 60% on vague input, 3 questions were asked, workflow stopped correctly until answers were received.
[example_1_tutoring_app.md](https://github.com/user-attachments/files/28444638/example_1_tutoring_app.md)

