# Alumni Portal

> **Naming note:** "alumni-connect" is a placeholder repo name. The project doesn't have a final name yet.

An alumni portal for KEC — Kumaon Engineering College, now BTKIT (Bipin Tripathi Kumaon Institute of Technology) — in Dwarahat, Almora, Uttarakhand. Most people still say KEC, so the docs do too. Built by KEC students with ColoredCow as mentors.

## The Problem

KEC's alumni network is fragmented. Students — especially the ones about to graduate — have no reliable way to reach alumni. Alumni who want to give back (advice, referrals, mentorship) have no reliable way in either. Both sides exist; the connection doesn't.

## Three Layers

The project is built on three layers at once:

1. **Solve KEC's problem.** A working alumni network for KEC comes first. If it doesn't work for KEC, nothing else matters.
2. **Build it as a product.** Generic from day one, so it can scale to other Uttarakhand colleges and institutions where networks matter. Nothing KEC-specific gets hardcoded.
3. **Build it AI-first.** AI inside the product (matching, search, profile help) and AI in how we build it (agentic development). We're not building a 10-year-old piece of software with today's tools.

## Think Big, Do Small

The vision is big; the steps are small. We pick one small, concrete module — most likely **data collection** — and ship it as a proof of concept to start the shipping cycle. Everything else grows from there.

There's precedent: ColoredCow built **Yearbook**, a data-collection and filtering tool for IIT Delhi, about 8–9 years ago (web + mobile data entry, hostel/branch filters). It's archived now, but its code is a starting point we can reuse. Same lesson applies here: start with the data, everything else comes after.

## Current Status

**Foundation phase.** We're laying down docs, structure, and open questions before writing application code. The first student cohort (CSE first-years) is currently paused for exams; work picks back up after.

Deliberately undecided right now:

- Final project / repo name
- Tech stack — see [docs/architecture.md](docs/architecture.md)
- V1 feature set — see [docs/architecture.md](docs/architecture.md) and [docs/research.md](docs/research.md)

## Repository Structure

```
README.md                  # You are here
TEAM.md                    # Who owns which thread + who has contributed
docs/
  architecture.md          # System design thinking (stack TBD)
  process.md               # How we work — SDLC, GitHub flow, weekly cadence
  best-practices.md        # Conventions, ownership norms, commit/PR hygiene
  research.md              # Open questions — data sources, integrations
  student-artifacts/       # Requirement docs from the first-years, kept as reference
```

All documentation lives in `docs/`. The root stays clean so application code can live here later.

## Team

- ColoredCow — mentors
- KEC students — the first cohort is CSE first-years; more join as the project grows

## Want to Contribute?

1. Read through `docs/` — start with [architecture.md](docs/architecture.md), then [process.md](docs/process.md).
2. Join the team channel (Google Chat) — ask any owner listed in [TEAM.md](TEAM.md) to add you.
3. Pick something small. An open question from [research.md](docs/research.md) is a good first thread.

You learn the project by contributing to it, not before contributing to it.
