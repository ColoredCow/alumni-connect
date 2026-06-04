# Best Practices

> Standards we follow — for code, docs, collaboration, and mindset.

## Mindset

- **Take ownership.** Whatever you are building, understand it fully. It is your product.
- **Don't panic on errors.** When something breaks, tell the team first. Then fix it together. Panic makes things worse.
- **Don't blindly use AI.** AI is great for repetitive tasks but will fail on unique problems requiring real thinking. You direct it — don't let it direct you. If you can't explain what the AI produced, don't ship it.
- **Ask questions. Don't assume.** Assumptions are the root of most bugs and miscommunication.

## Ownership Norms

Areas of the project have named owners — see [TEAM.md](../TEAM.md).

- **Owning a thread means keeping it moving and visible** — making sure it progresses, decisions get made, and the team knows where it stands. It does **not** mean doing it alone.
- Everyone discusses and contributes to every area. The owner is the one accountable for the thread not stalling or going silent.
- If you're an owner and you're stuck, raise it — early and out loud. A blocked thread the team knows about is fine; a quiet one isn't.

## Code Practices

- All code goes through GitHub. No exceptions.
- Every feature gets its own branch.
- PRs are reviewed before merging.
- No hardcoding of KEC-specific values — think generic from day one.
- Write comments for anything non-obvious.

## Commit & PR Hygiene

**Commits**

- Small, focused commits — one logical change per commit.
- Messages say *what changed and why*, not "fix" or "update stuff". Example: `Add open question on TPO data sharing to research.md`.
- Commit docs and decisions, not just code.

**Branches**

- Branch from `main`, name by what the branch does: `docs/process-update`, `research/erp-question`, later `feature/...`.

**Pull requests**

- Keep PRs small enough to actually review.
- Description covers what changed and why; link the doc, question, or issue it relates to.
- At least one review before merge. Don't merge your own PR unreviewed.
- Respond to review comments — resolve them or push back, but don't ignore them.

## Review Practice

When reviewing anyone's work — PRs, docs, designs — follow this order:

1. **Lead with what's working.** Name the things that are good and should stay.
2. **Then where to push.** Concrete, specific suggestions — not vague discomfort.
3. **End with questions.** What you don't understand, or want the author to think harder about.

Reviews exist to make the work better, not to prove the reviewer is smart.

## Documentation Practices

- Keep docs updated as decisions change — these are living documents.
- Write from the project's perspective, not your personal perspective.
- **One shared file per area** — no per-person files, no per-person sections. Contributions merge into the shared doc.
- One doc per concern — don't mix architecture with process.
- Where something isn't decided, write an explicit `TODO` or open question. Don't guess and present it as decided.
- Plain, honest language. No filler, no marketing tone.
- If you're unsure whether to document something, document it.

## Recommended Reading

- *The Pragmatic Programmer* — ownership, care, craftsmanship in software
