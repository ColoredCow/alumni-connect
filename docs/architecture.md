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

- **Alumni** — maintain a profile, find batchmates, give back (mentorship, referrals, talks)
- **Students** — discover and reach relevant alumni by branch, domain, company, batch
- **Admin** — manage data, moderate content, run the platform for their institution

## Modules (proposed — V1 not finalized)

> **TODO:** V1 scope is not locked. This list is current thinking, not a commitment. The V1/V2/V3 split below is a working sketch.

- **Data Collection (likely V1, and the proof-of-concept module)** — onboarding alumni, collecting profile info
- **Alumni Directory (likely V1)** — search/filter by branch, batch, company, domain
- **Student–Alumni Connect (later)** — messaging, mentorship requests
- **Admin Dashboard (later)** — manage entries, moderate content
- **Yearbook / Book Export (later)** — generate printable alumni booklet (like IIT Delhi)

**Why data collection first:** the network is only as good as its data — without profiles there is nothing to search, match, or connect. Same lesson as the IIT Delhi Yearbook tool: start with data collection, everything else grows from there.

## System Design

> **TODO:** placeholder — to be filled once the data-collection module is scoped and the stack is chosen. Expected sections:

- **Data model** — what an alumni profile is; college-agnostic from the start (see research question on a generic data model)
- **High-level components** — data entry (web + mobile), storage, search/filtering, admin
- **AI inside the product** — where AI features plug in (early ideas in [research.md](research.md))
- **Multi-college / multi-tenant thinking** — how one deployment serves many institutions later, without over-engineering V1

## Data Sources

Where alumni data actually comes from (ERP integration, TPO data, self-upload vs. data entry) is an open question, tracked in [research.md](research.md). The answer shapes the data-collection module, so research feeds architecture directly.

## Reference: Yearbook (IIT Delhi)

Built by ColoredCow ~8–9 years ago for IIT Delhi — data collection, filtering, and categorization with web + mobile data entry and hostel/branch filters. Archived, but the codebase is available and can be reused as a starting point for our data-collection module.

See [alumni-booklet.md](../artifacts/alumni-booklet.md) for the full data field reference.

## Tech Stack

> **TODO:** not chosen. Will be decided alongside V1 scope. Constraints to evaluate against:

- Keep it simple for V1
- Should support web + mobile data entry
- AI integration considered from day one (inside the product, not just in the process)
- Generic / configurable — nothing that locks us to KEC
