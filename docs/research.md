# Research

> Open questions, things to investigate, references to explore. Questions stay framed **as questions** until they're actually answered — don't write answers in here that haven't been verified.
>
> Owners of this thread: see [TEAM.md](../TEAM.md) (Requirement / research).

## Open Questions

> One status per item: **Open** → **Investigating** → **Answered** (with a link or note).

### Data — the questions that shape V1

1. Where will the alumni data come from — what sources actually exist today? — **Open**
2. Does the college already hold student/alumni data in an ERP or any existing system? — **Open**
3. If an existing system holds the data, is integration with it possible — technically and politically? — **Open**
4. Who uploads the data, and how — alumni self-serve, a student team doing data entry, the college/TPO handing over records? — **Open**
5. Will the college share data, or will users upload it themselves? Is uploading actually easy for them? — **Open**
6. What alumni data does the TPO already have, and will they share it? — **Open**

### Product & reference

7. What's reusable from the IIT Delhi Yearbook tool — both the code and the booklet process? — **Open**
8. How do IITs manage their alumni networks? (IIT Delhi as reference) — **Open**
9. What existing alumni portal products are out there? (Pros/cons vs building our own) — **Open**
10. What does a "college-agnostic" data model look like? (for scaling beyond KEC) — **Open**

### Technical (feeds the stack decision)

11. Authentication options — Google SSO, college email login? — **Open**
12. Mobile-first vs web-first for alumni data entry? — **Open**

## Inputs

- Initial thinking, ideas, and early requirement docs are kept in [artifacts/](../artifacts/) — raw material for the questions above.

## Reference Projects

### IIT Delhi Yearbook Tool (ColoredCow)

- Built ~8–9 years ago for IIT Delhi's 25-year alumni booklet
- Features: profile creation, photo upload, search, hostel/branch filters, mobile + web data entry
- Purpose: data collection and management for printing physical alumni booklets
- Status: archived, codebase available for reference and reuse as a starting point
- Lesson: start with data collection, everything else comes after

## Market Context

- Alumni networking is largely unsolved for tier 2/3 colleges
- KEC founded 1992 — 30+ years of alumni across many domains
- Opportunity to expand beyond KEC → other Uttarakhand colleges → other institutions

## AI Integration Ideas (early thoughts, not commitments)

- AI-assisted profile completion (suggest what to fill based on partial data)
- Smart matching between students and relevant alumni mentors
- Auto-categorization of alumni by domain/role from LinkedIn-style data
