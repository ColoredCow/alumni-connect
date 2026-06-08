# Architecture

> Living document. Nothing here is final — the tech stack is not chosen and the V1 feature set is not locked. `TODO` marks what's open. Update this as decisions are made.

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
- Search / filter alumni by year, name, or branch — including an agentic angle, e.g. a chat box: "give me all CSE alumni."

**Why data collection first:** the network is only as good as its data — without profiles there is nothing to search, match, or connect. Same lesson as the IIT Delhi Yearbook tool: start with data collection, everything else grows from there.

> **TODO — still open:**
> - Which users are in V1 — college only, or college + alumni + students together? (Undecided — students may be out of V1.)
> - Verification — how do we confirm someone is actually a KEC alumnus?

## System Design

> **TODO:** placeholder — to be filled once the data-collection module is scoped and the stack is chosen. Expected sections:

- **Data model** — what an alumni profile is; college-agnostic from the start (see research question on a generic data model)
- **High-level components** — data entry (web + mobile), storage, search/filtering, admin
- **AI inside the product** — where AI features plug in (early ideas in [research.md](research.md))
- **Multi-college / multi-tenant thinking** — how one deployment serves many institutions later, without over-engineering V1. Direction: the same codebase with a separate database per college; college-specific things — name, logos, branding, config — come from the database / config, never hardcoded. BTKIT / KEC is the first customer, not the only one.

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

> **TODO:** not chosen. Will be decided alongside V1 scope. Constraints to evaluate against:

- Keep it simple for V1
- Should support web + mobile data entry
- AI integration considered from day one (inside the product, not just in the process)
- Generic / configurable — nothing that locks us to KEC
