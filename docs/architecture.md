# Architecture

> This is a living document. Update it as decisions are made.

## Problem Statement

KEC has a fragmented alumni network. Students graduating don't have a way to connect with seniors, and alumni don't know how to give back. This portal solves both sides of that equation.

## High-Level Goals

- Alumni can create and maintain profiles
- Students can discover and connect with alumni (by branch, domain, company, batch)
- Data collection is easy — for admins, alumni, and the college
- The platform is generic enough to be used by other colleges

## Target Users

- **Alumni** — maintain a profile, find batchmates, give back (mentorship, referrals, talks)
- **Students** — discover and reach relevant alumni by branch, domain, company, batch
- **Admin** — manage data, moderate content, run the platform for their institution

## Product Stance

This is a **generic product, not a KEC project**. KEC is the first deployment, not the definition — no KEC-specific values get hardcoded anywhere. Target path: KEC → other Uttarakhand colleges → institutions beyond.

## Core Modules (thinking phase)

- **Data Collection (V1)** — onboarding alumni, collecting profile info
- **Alumni Directory (V1)** — search/filter by branch, batch, company, domain
- **Student-Alumni Connect (V2)** — messaging, mentorship requests
- **Admin Dashboard (V2)** — manage entries, moderate content
- **Yearbook / Book Export (V3)** — generate printable alumni booklet (like IIT Delhi)

**First module: Data Collection.** Why first: the network is only as good as its data — without profiles there is nothing to search, match, or connect. (Same lesson as the IIT Delhi Yearbook tool: start with data collection, everything else grows from there.)

## Data Sources

Open questions about where alumni data comes from (ERP integration, TPO data, self-upload vs. data entry) are tracked in [research.md](research.md).

## Reference

- IIT Delhi Yearbook tool (built by ColoredCow ~8-9 years ago) — data collection + filtering + categorization. Codebase available for reference.

## Tech Stack

> To be decided. Will update once foundation is clearer.

- Keep it simple for V1
- Should support web + mobile data entry
- AI integration to be considered from day one (inside product, not just in process)
