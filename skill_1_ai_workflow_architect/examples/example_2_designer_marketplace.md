# Example 2 — Freelance Designer Marketplace

## Input

"I want to create a Marketplace for freelance designers. It should be both web and mobile version. No specific constraints."

---

## Step 1 — Intent Extraction

- **Project Type:** Freelance Marketplace
- **Platform:** Web (Responsive/PWA) + Mobile (iOS/Android)
- **Complexity:** High — user profiles, portfolio management, search/discovery, messaging, payment processing, dispute resolution
- **Target Users:** Freelance Designers (sellers) and Clients/Businesses (buyers)
- **Core Integrations:** Payment Gateway (Stripe/PayPal), Cloud Storage (AWS S3 for portfolios), Real-time Messaging (Socket.io/Firebase), Email/Push Notifications

**Confidence: 70%**
Reason: Platform and user types are clear, but monetization model and design specialty focus are unknown — both materially affect the data model and features.

---

## Step 2 — Clarification Agent

2 questions asked (confidence sufficient for most decisions, only 2 blockers):

1. **Monetization:** Will the platform take a commission on transactions, charge subscription fees, or both?
2. **Design Focus:** Is there a specific niche (e.g., UI/UX, branding, illustration) or is it general design?

User answered: "Subscription model $5–$20–$50 tiers. Focus on branding/logo/brand colours/merch."

---

## Step 3 — Architecture Generation

### Tech Stack

| Layer | Selected | Why | Alternative |
|-------|----------|-----|-------------|
| Frontend | React + PWA | Shared codebase, offline support | Next.js |
| Mobile | React Native | Shared business logic with web | Flutter |
| Backend | Node.js + NestJS | Modular, scalable, TypeScript | Django |
| Database | PostgreSQL | Relational data for users, subscriptions, orders | MySQL |
| Storage | AWS S3 | High-res design asset storage | Cloudinary |
| Payments | Stripe | Subscription management, marketplace payouts | PayPal |
| Real-time | Socket.io | Client-designer messaging | Firebase Realtime |
| Search | Elasticsearch | Portfolio search by specialty/style | Algolia |

### Core Modules

- **Auth & Profiles** — Designer portfolios (branding focus), Client profiles
- **Subscription Engine** — Tiered access ($5 Basic / $20 Pro / $50 Enterprise)
- **Portfolio Manager** — Branding/logo/merch project showcase, high-res uploads
- **Search & Discovery** — Filter by specialty, style, rating, subscription tier
- **Order/Project Workflow** — Briefing → Concept → Revision → Delivery
- **Asset Vault** — Secure file delivery (SVG, AI, PNG) with pre-signed S3 URLs
- **Messaging** — Threaded, milestone-linked conversations
- **Review & Rating** — Post-delivery client reviews

### API Structure

```
POST   /auth/register
GET    /designers?specialty=branding&tier=pro
GET    /designers/:id/portfolio
POST   /subscriptions/subscribe
POST   /orders/create
GET    /orders/:id/status
POST   /messages/send
GET    /assets/:orderId
POST   /reviews/submit
```

### DB Schema

**Users:** id, role (designer/client), email, subscription_tier, created_at
**Designers:** id, user_id, specialty, bio, rating, portfolio_items (JSONB)
**Orders:** id, client_id, designer_id, status, brief (JSONB), price, created_at
**Assets:** id, order_id, file_url (S3), type (svg/ai/png), version, uploaded_at
**Messages:** id, order_id, sender_id, content, file_attachment, created_at
**Subscriptions:** id, user_id, tier, stripe_subscription_id, status, expires_at

Indexes: specialty + rating on Designers, status on Orders, order_id on Messages
Scaling: S3 pre-signed URLs for direct asset downloads, CDN for portfolio images

---

## Step 4 — Execution Planning

### MVP Roadmap

**Phase 1 (Weeks 1–3):** Auth, Designer profiles, Subscription tiers via Stripe
**Phase 2 (Weeks 4–6):** Search/Discovery (branding/logo/merch categories), Order workflow
**Phase 3 (Weeks 7–8):** Real-time messaging, Asset Vault delivery
**Phase 4 (Weeks 9–10):** Mobile app, Reviews, Analytics

### Priority Order

1. Auth & Profiles — no marketplace without users
2. Subscription Engine — monetization is core, not optional
3. Portfolio Manager — designers need this before clients can discover them
4. Search & Discovery — depends on populated portfolios
5. Order Workflow — depends on both parties being registered
6. Asset Vault — depends on order completion flow
7. Messaging — depends on active orders
8. Mobile App — depends on stable web API

---

## Step 5 — LLM Critic

**Risk 1 — Technical / High**
High-resolution design files (AI, PSD) can be 100MB+. Standard file upload flows will fail or timeout.
Mitigation: Use S3 multipart upload with presigned URLs, implement client-side chunking, set size limits per subscription tier.

**Risk 2 — Business / Medium**
Subscription churn risk — designers may not see enough clients to justify $20–$50/month early on.
Mitigation: Launch with a free tier for designers, charge clients on transaction commission initially, introduce subscriptions after marketplace liquidity is proven.

**Risk 3 — Compliance / Medium**
Marketplace platforms with payments are subject to KYC/AML requirements for designer payouts in most jurisdictions.
Mitigation: Use Stripe Connect with built-in KYC flow, restrict payouts to jurisdictions where Stripe Connect is available, consult legal before launch.

---

## Outcome

Full pipeline executed in one run. Confidence was 70% — only 2 questions asked (not 3) because most architecture was determinable from the input. Adaptive behavior confirmed.
[example_2_designer_marketplace.md](https://github.com/user-attachments/files/28444644/example_2_designer_marketplace.md)

