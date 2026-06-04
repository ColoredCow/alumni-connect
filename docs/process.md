# Process

> How we work — SDLC, communication, and collaboration norms. Placeholders are marked `TODO` where decisions are pending.

## Development Philosophy

- **Think big, do small.** Don't try to build everything at once. Pick the smallest concrete module and ship it.
- **Shipping cycle matters.** A month of planning with no output kills momentum. Keep the cycle short.
- **AI-first.** Use AI throughout the build process, but apply your own critical thinking for direction and decisions. AI handles repetition and speed; you handle judgment.

## SDLC — Adapted for an AI-First Workflow

We follow the normal software development lifecycle, with AI/agentic tooling woven into each stage. The stages don't change; how fast and how we move through them does.

| Stage | What happens | Where AI fits |
|---|---|---|
| Requirements | Open questions answered in [research.md](research.md); requirements written down before building | Drafting, summarizing research; the team validates with real people |
| Design | Architecture and data model sketched in [architecture.md](architecture.md) | Exploring options, pressure-testing designs; humans decide |
| Build | Small modules, own branch, PR | Agentic coding — AI writes a lot of the code; you direct, review, and understand all of it |
| Review | Every PR reviewed before merge | AI-assisted review is fine; a human reviewer is still required |
| Ship | Staging first, then production | TODO: deployment automation — decided with the stack |

Rule of thumb: AI accelerates every stage, but every stage still has a human who understands and owns the output. If you can't explain what the AI produced, it doesn't merge.

## GitHub Flow

- `main` stays stable. Every change — docs or code — happens on its own branch.
- Branches merge into `main` through a PR. Every PR is reviewed before merging (see [best-practices.md](best-practices.md) for commit/PR hygiene and how we review).
- Commit everything the project needs to remember: docs, decisions, designs, code. If it only lives in someone's head or a chat thread, it doesn't exist.

## Staging Before Production

Once we have code, changes deploy to a **staging** environment first; after verification there, they get promoted to the hosted (production) site. Nothing goes straight to production.

> **TODO:** hosting platform and staging setup — decided with V1 scope and stack.

## Committed Timelines

Dates here are commitments, not estimates we quietly let slide.

- Every milestone gets an owner and a target date.
- If a date is going to slip, the owner says so **early** — before the date, not after. Slipping with notice is normal; going silent is not.

### Milestones

> **TODO:** target dates to be committed.

| Milestone | What it means | Target date | Owner |
|---|---|---|---|
| Foundation | Docs, GitHub structure, research questions framed | TODO | TODO |
| V1 scope locked | Decide what's in V1 | TODO | TODO |
| V1 design | Basic wireframes / flows | TODO | TODO |
| V1 development | Build the V1 module(s) | TODO | TODO |
| V1 launch | Hosted, announced to the college | TODO | TODO |

## Weekly Consolidated Update

Once a week, **one** consolidated update goes to the team — not ten scattered messages.

- Each area owner (see [TEAM.md](../TEAM.md)) sends their thread's status to whoever is consolidating that week.
- The consolidated update covers: what was done, what's next, what's blocked.
- It gets posted to the WhatsApp group (broader student group) and the work channel.

> **TODO:** who consolidates (rotating vs. fixed) and which day of the week — to be decided.

## Onboarding — Getting on a Moving Bus

The project keeps moving; new contributors get on the bus while it's rolling. To join:

1. Read `docs/` end to end (architecture → process → best-practices → research), plus [TEAM.md](../TEAM.md) at the root.
2. Sit in on a weekly sync. Listen first, ask questions after.
3. Pick the smallest open item — a research question, a doc fix — and own it end to end.
4. Post your first update in the weekly thread.

You learn the project by contributing to it, not before contributing to it. The initial thinking and ideas in [artifacts/](../artifacts/) are worth a skim to see where the project started.

## Communication Channels

- **Google Chat** — primary work communication
- **WhatsApp group** — announcements, weekly updates to the broader student group
- **GitHub** — all project artifacts, decisions, code
- **Google Meet** — sync calls with the ColoredCow team

## Working Norms

- Every **task** has one owner who keeps it moving (area ownership works the same way — see [TEAM.md](../TEAM.md)).
- If you're blocked, say it out loud. Don't silently drop a task.
- If a mistake happens, **communicate first, fix second.** Don't panic and go silent.
