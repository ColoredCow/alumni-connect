# Process

> How we work — SDLC, communication, and collaboration norms.

## Development Philosophy

- **Think big, build small.** Don't try to build everything at once. Pick the smallest concrete module and ship it.
- **Shipping cycle matters.** A month of planning with no output kills momentum. Keep the cycle short.
- **AI-first.** Use AI in the build process, but apply your own critical thinking for direction and decisions. AI handles repetition; you handle thinking.

## Workflow

1. **Document first** — Before writing code, write what you're building in `/docs`.
2. **GitHub as source of truth** — All ideas, decisions, architecture thoughts go here.
3. **Weekly updates** — Post a consolidated update to the WhatsApp group every week. What was done, what's next.
4. **Iterations** — Build in small versions: V1 → V2 → V3. Define what's in each.

## GitHub Workflow

- `main` stays stable. Every change — docs or code — happens on its own branch.
- Branches merge into `main` through a PR. Every PR is reviewed before merging (see [best-practices.md](best-practices.md) for how we review).
- Commit everything the project needs to remember: docs, decisions, designs, code. If it only lives in someone's head or a chat thread, it doesn't exist.
- **Staging → hosting:** once we have code, changes deploy to a staging environment first; after verification there, they get promoted to the hosted (production) site. Hosting platform TBD — decided with V1 scope.

## Onboarding — Getting on a Moving Bus

The project keeps moving; new contributors get on the bus while it's rolling. To join:

1. Read `/docs` end to end (architecture → process → best-practices → research).
2. Sit in on a weekly sync. Listen first, ask questions after.
3. Pick the smallest open item — a research question, a doc fix — and own it end to end.
4. Post your first update in the weekly thread.

You learn the project by contributing to it, not before contributing to it.

## Milestones (to be filled)

- **Foundation** — docs, GitHub structure, research. Target date: TBD
- **V1 Scope locked** — decide what goes in V1. Target date: TBD
- **V1 Design** — basic wireframes/flows. Target date: TBD
- **V1 Development** — build V1 modules. Target date: TBD
- **V1 Launch** — hosted, announced to college. Target date: TBD

## Communication Channels

- **Google Chat** — Primary work communication
- **WhatsApp Group** — Announcements, updates to broader student group
- **GitHub** — All project artifacts, decisions, code
- **Google Meet** — Sync calls with ColoredCow team

## Ownership Rules

- Every task must have **one owner**. Not two, not "someone."
- If you're blocked, say it out loud. Don't silently drop a task.
- If a mistake happens, **communicate first, fix second.** Don't panic and go silent.
