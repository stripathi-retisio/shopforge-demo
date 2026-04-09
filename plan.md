# PLAN.md — Project Plan

## Vision

Build a self-serve, multi-tenant ecommerce platform that proves the full product thinking behind SaaS — from merchant onboarding and storefront isolation, to platform-level admin controls and a real-world database schema.

The goal isn't just a demo. It's a foundation that could be wired to a real backend and taken to production.

---

## Problem Statement

Most ecommerce demos show a single store. They don't address the **multi-tenancy problem** — how do you let hundreds of merchants each run their own independent store, with their own products, orders, branding, and settings, all on one platform?

ShopForge solves this end-to-end — in the UI, in the data model, and in the architecture.

---

## Scope

### In Scope (v1 — current)

| Area | What's Built |
|---|---|
| Merchant onboarding | 4-step self-serve signup with theme picker |
| Merchant dashboard | Products CRUD, orders management, store settings |
| Public storefront | Per-tenant branded store, cart, checkout |
| Admin dashboard | Cross-tenant merchant/order/revenue oversight |
| Data layer | localStorage mock DB with full relational schema |
| DB schema | Production-ready PostgreSQL schema documented |
| Routing | SPA router (no page reloads, no URL hash) |

### Out of Scope (v1)

- Real backend / database (localStorage only)
- Payment processing
- Image uploads
- Email notifications
- Custom domains
- SEO / server-side rendering
- Mobile app

---

## Phases

### Phase 0 — Design & Architecture ✅
- Define multi-tenancy strategy (tenant ID scoping)
- Design relational schema (tenants, products, orders, admins, sessions, plans)
- Choose tech stack (plain HTML/CSS/JS for zero-friction demo)
- Map all user flows (merchant, customer, admin)

### Phase 1 — Core Platform ✅
- SPA router with view switching
- localStorage DB layer (get, set, seed)
- Merchant signup + login
- Merchant dashboard shell with sidebar navigation

### Phase 2 — Merchant Features ✅
- Product add / edit / delete / publish-toggle
- Order listing with status filters
- Order status update
- Store settings (name, slug, brand color, feature toggles)
- Danger zone (delete store)

### Phase 3 — Storefront ✅
- Per-tenant public storefront with brand theming
- Product catalog
- Cart sidebar with quantity controls
- Checkout modal + order placement
- Order confirmation

### Phase 4 — Admin Dashboard ✅
- Platform stats (revenue, stores, orders)
- Merchant table with suspend/activate/delete
- Plan distribution visualization
- Cross-tenant order ledger

### Phase 5 — Backend (Planned)
- [ ] Node.js + Express REST API
- [ ] PostgreSQL with Row-Level Security per tenant
- [ ] JWT-based auth (access + refresh tokens)
- [ ] Merchant session management
- [ ] API endpoints for all CRUD operations

### Phase 6 — Production Features (Planned)
- [ ] Razorpay / Stripe payment integration
- [ ] Image uploads (Cloudinary or S3)
- [ ] Email notifications (Resend / SendGrid)
- [ ] Custom subdomain per store (slug.shopforge.io)
- [ ] Webhook support for order events
- [ ] Analytics (real time-series revenue data)

### Phase 7 — Scale (Future)
- [ ] App marketplace / plugin system
- [ ] Storefront theme builder (drag-and-drop)
- [ ] Multi-currency support
- [ ] Inventory alerts
- [ ] Affiliate / referral system
- [ ] Mobile apps (React Native)

---

## Success Metrics (v1)

| Metric | Target |
|---|---|
| Merchant can sign up and launch a store | < 2 minutes |
| Merchant can add a product | < 30 seconds |
| Customer can find and order a product | < 3 clicks |
| Admin can see all platform activity | Single view |
| DB schema can migrate to real Postgres | Zero changes needed |

---

## Risks & Mitigations

| Risk | Mitigation |
|---|---|
| localStorage has 5MB limit | Fine for demo; production uses Postgres |
| No real auth (passwords stored in plain text) | Documented — production uses bcrypt + JWT |
| No real payments | Checkout UI is complete; payment gateway is a drop-in |
| Single HTML file gets unwieldy | Phase 5 splits into proper frontend + API |

---

## Decision Log

| Decision | Rationale |
|---|---|
| Single HTML file | Zero setup friction — anyone can open it, fork it, deploy it |
| localStorage DB | Lets the schema and data model shine without backend complexity |
| Vanilla JS (no framework) | Demonstrates the router, state, and DOM logic from first principles |
| INR as default currency | Built for the Indian market; trivially configurable |
| Emoji as product images | No image upload infra needed for a prototype |
