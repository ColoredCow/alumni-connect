# Architecture

> Living document. `TODO` marks what is still open. Update this as decisions are made.

## Problem Statement

KEC's alumni network is fragmented. Students graduating don't have a way to connect with seniors, and alumni don't know how to give back. This portal solves both sides of that equation.

## How the Three Layers Shape Decisions

Every architecture decision gets checked against the three layers the project is built on:

1. **Solve KEC's problem first.** If a feature doesn't help KEC students and alumni connect, it doesn't belong in V1. KEC is the proving ground — a design that's elegant but doesn't work for KEC is the wrong design.
2. **Generic product from day one.** KEC is the first deployment, not the definition. No KEC-specific values hardcoded anywhere — college name, branches, batches, departments all come from data or config. Target path: KEC → other Uttarakhand colleges → institutions beyond.
3. **AI-first.** When evaluating any stack or design choice, ask: does it make it easy to put AI inside the product (matching, profile completion, search), and does it work well with agentic AI development? We're building software for now, not repeating a 10-year-old pattern.

## Target Users

All three user types below still matter, but for V1 they are **not equal**: the **college — the TPO / admin — is the primary user**, ahead of students and alumni. This prioritization is decided; whether it's feasible is not yet confirmed (see the note below).

- **College / TPO (admin) — primary for V1.** Has a concrete, recurring need: keep alumni data in one place, use it to market the college ("our alumni are at X and Y"), connect with alumni to run workshops, and let the TPO reach companies and CEOs directly for placements. It replaces today's mess — scattered Google Forms, random personal QR codes for payments, alumni data spread across different people.
- **Alumni** — maintain a profile, find batchmates, give back (mentorship, referrals, talks). Real value, but irregular use — not a daily-use audience.
- **Students** — discover and reach relevant alumni by branch, domain, company, batch. A student who really wants to reach an alumnus can already do this on LinkedIn (filter by college), so a student-first portal adds little over what exists — the "connect" step is the same chat either way.

**Why the college comes first**

- **Dependency.** You can't start with students — students need alumni already on the platform to connect with. Alumni data has to come first, and the college is the route to that data.
- **One platform, not three apps.** Don't model students and alumni as separate populations — the same person is a student today and an alumnus tomorrow. Treat student / alumni / college as roles (tags) on one platform.

> **Note — decided, but feasibility pending.** The prioritization above is our decision. It rests on something we haven't verified: that the alumni data exists and that the college will share it. That discovery is tracked in [research.md](research.md). Until we know, treat "build for the college first" as our chosen direction, not a confirmed plan.

## Modules (proposed — V1 not finalized)

> **TODO:** V1 scope is not locked. This list is current thinking, not a commitment. The V1/V2/V3 split below is a working sketch.

V1 is anchored on the college (TPO / admin) as the primary user — see **Target Users** above. The modules below are framed around what the college needs first.

- **Data Collection (likely V1, and the proof-of-concept module)** — onboarding alumni, collecting profile info
- **Alumni Directory (likely V1)** — search/filter by branch, batch, company, domain
- **Student–Alumni Connect (later)** — messaging, mentorship requests
- **Admin Dashboard (later)** — manage entries, moderate content
- **Yearbook / Book Export (later)** — generate printable alumni booklet (like IIT Delhi)

**What the TPO can do in V1 (proposed):**

- See the full alumni list; filter by year / session / branch.
- Manually add new alumni — the TPO holds the records, especially for recent placements.
- Send an invite link to an alumnus to create or update their own profile.
- Search / filter alumni by year, name, or branch.

**Why data collection first:** the network is only as good as its data — without profiles there is nothing to search, match, or connect. Same lesson as the IIT Delhi Yearbook tool: start with data collection, everything else grows from there.

> **TODO — still open:**
> - Which users are in V1 — college only, or college + alumni + students together? (Undecided — students may be out of V1.)
> - Verification — how do we confirm someone is actually a KEC alumnus?

## System Design

> **TODO:** Data model and high-level component diagrams to be filled once V1 scope is locked. Multi-tenancy strategy and AI insertion points are decided below.

### Multi-college / multi-tenant

One codebase serves many colleges. Each college gets its own subdomain (`kec.app`, `gbu.app`), its own database, and its own config (name, logo, colours, SMTP) — nothing is hardcoded to KEC.

**Migration path — start simple, scale when needed:**

| Stage | Strategy |
|---|---|
| V1 — KEC alone | Single shared database with a `college_id` column. Zero operational overhead. |
| 3–10 colleges | Switch to database-per-college using `stancl/tenancy`. Same codebase, same package — config change only. |
| 100+ colleges | Horizontal database sharding across servers. Far future. |

Tenant routing is subdomain-based. Per-college config (branding, SMTP, feature flags) lives in the tenant's database record, never in code.

### AI insertion points (future — not V1)

AI is out of V1 scope but the stack is chosen to make it straightforward to add later:

| Feature | How it plugs in |
|---|---|
| Profile auto-completion | Laravel job → LLM API call via Laravel Prism |
| Alumni–student matching | Profile embeddings stored in PostgreSQL via pgvector → similarity query |
| Natural language search | Query → LLM → SQL/vector search → results |
| Yearbook PDF export | Queued Laravel job → DomPDF/Snappy (no AI needed) |

All of this runs inside the existing Laravel app — no separate Python service, no new infrastructure.

## Data Sources

Where alumni data actually comes from (ERP integration, TPO data, self-upload vs. data entry) is an open question, tracked in [research.md](research.md). The answer shapes the data-collection module, so research feeds architecture directly.

**Candidate approaches for getting the first records in** — options under consideration, pending the TPO discovery in [research.md](research.md). None is decided:

- TPO adds alumni manually.
- TPO sends invite links → alumni self-create their profiles.
- Seed the database by extracting from existing Excel sheets / registers.
- Current students as the initial seed — student emails are already being collected across years (a record of ~300 up to second year is on its way; the current session's data will be completed via the college). The easy first entries are current students who later become alumni; the hard part is old / historical alumni.
- A batch-email feature so the TPO can invite a whole batch at once.

## Reference: Yearbook (IIT Delhi)

Built by ColoredCow ~8–9 years ago for IIT Delhi — data collection, filtering, and categorization with web + mobile data entry and hostel/branch filters. Archived, but the codebase is available and can be reused as a starting point for our data-collection module.

See [alumni-booklet.md](../artifacts/reference/alumni-booklet.md) for the full story of what ColoredCow built.

## Tech Stack

**Decided.** The stack below is the result of research across six dimensions: frontend performance on low-end devices and slow networks (the primary constraint for Tier 2/3 college TPOs), admin/CRUD tooling maturity (V1 is an admin tool first), multi-tenancy operational simplicity, hosting cost in the Indian context, AI-readiness for the future roadmap, and mentorability for a junior team.

### Backend — Laravel (PHP)

Laravel is the application framework. It handles routing, business logic, authentication, queues, background jobs, email, and API endpoints. The ORM is Eloquent (built in — no separate layer needed). Multi-tenancy runs via the `stancl/tenancy` package, which supports both shared-DB and DB-per-tenant strategies from the same codebase.

**Why Laravel over Django:** ColoredCow has shipped both (Plio on Django + Vue, IAGES on Laravel). The decisive factors for this product are:
- `stancl/tenancy` is more flexible than `django-tenants` — supports both shared DB and DB-per-tenant, switchable without a rewrite. `django-tenants` locks you to PostgreSQL schema-per-tenant from day one.
- Filament (see below) has no equivalent in the Django ecosystem for product-grade admin UIs.
- Laravel runs on shared PHP hosting — cheapest entry point for a college-budget product in India.

### Admin panel — Filament v5

Filament is built on top of Laravel + Livewire + Alpine.js + Tailwind CSS. It ships tables, forms, filters, bulk actions, modals, and a dashboard shell — all defined in PHP, zero JavaScript to write. V1's TPO-facing interface is essentially Filament wired to the alumni data models.

**UI quality:** Filament's default look is clean and functional but recognisable. Apply the [shadcn theme for Filament](https://filamentphp.com/plugins/openplain-shadcn-theme) or [Aura UI](https://aura-ui.com/filament) (8 modern presets including glassmorphism, midnight dark, minimal) to match 2026 SaaS product aesthetics. Full dark mode is built in.

### Frontend for user-facing pages — Svelte 5 + Inertia.js

The TPO admin panel runs on Filament. Alumni and student-facing pages (profile creation, invite landing, public directory, messaging) use Svelte 5 via Inertia.js — Laravel's officially supported Svelte starter kit shipped February 2026.

Svelte ships 15–40 KB of JavaScript (vs React's 70–130 KB), compiles to vanilla JS at build time, and uses the shadcn-svelte + Tailwind CSS design system — the same visual language as modern SaaS products. It runs well on low-end devices and older browsers. Inertia.js means there is no separate API — Svelte components talk directly to Laravel controllers.

```
TPO admin panel            →  Filament + Livewire  (data-dense, CRUD-optimised)
Alumni / student pages     →  Svelte 5 + Inertia   (product-grade, lightweight)
Real-time chat / notifs    →  Laravel Reverb        (self-hosted WebSockets)
```

All three run inside the same Laravel application. One deployment.

### Real-time — Laravel Reverb

Reverb is Laravel's first-party, self-hosted WebSocket server. It powers real-time notifications, direct messaging, and live feed updates. A single instance handles ~1,000 concurrent connections per CPU core; scales horizontally with Redis pub/sub. No per-message billing (unlike Pusher or Ably). This is the foundation for LinkedIn-like interactions in later milestones.

### Database — PostgreSQL

PostgreSQL is chosen over MySQL for one forward-looking reason: the `pgvector` extension lets you store and query AI embeddings natively without adding a separate vector database. This is the direct path to alumni matching, natural language search, and profile completion in future milestones. Standard relational features (indexes, constraints, full-text search) cover everything V1 needs.

### AI — Laravel Prism (future, not V1)

Laravel Prism is a provider-agnostic LLM integration layer supporting 14 providers (OpenAI, Anthropic, Gemini, Groq, etc.) with automatic failover. It runs inside the existing Laravel app — no Python microservice, no new infrastructure. Combined with pgvector on PostgreSQL, it covers the full AI roadmap: embeddings, matching, completion, and natural language search.

### Full picture

```
Browser (TPO laptop / alumni phone)
         │  Filament: ~40 KB JS   /   Svelte pages: 15–40 KB JS
         ▼
  Filament + Livewire + Blade       Svelte 5 + Inertia.js
  (admin panel — TPO)               (user pages — alumni, students)
         │                                    │
         └──────────────┬─────────────────────┘
                        ▼
                 Laravel (PHP)
         routing · auth · business logic
         queues · jobs · email · Reverb
         stancl/tenancy (college routing)
                        │
                        ▼
                  PostgreSQL
          alumni data · college config
          pgvector (AI embeddings later)
```

### Constraints this stack was evaluated against

- **Low-end devices and old browsers** — Filament's reduced JS bundle and Svelte's compiled 15–40 KB output both work on weak hardware and slow networks. No heavy SPA framework shipped to the client.
- **Multi-tenancy** — `stancl/tenancy` is the 2026 production standard, used by thousands of SaaS platforms. Start with shared DB, graduate to DB-per-college when needed, same package.
- **V1 simplicity** — Filament means the TPO admin panel is days of work, not weeks. No frontend build complexity for V1.
- **Hosting cost** — PHP runs on shared hosting anywhere in India. Hostinger VPS from ~₹400/month covers a multi-college early deployment.
- **AI-readiness** — Laravel Prism + pgvector covers the full AI roadmap without a separate service.
- **Scalability** — same stack has run real-time social platforms, SaaS products at hundreds of thousands of users, and multi-tenant systems with 1,000+ tenants in production.
