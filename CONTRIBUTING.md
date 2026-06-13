# Contributing to Alumni Connect

## Communication Process

All project communication happens in the `#alumni-connect` Google Chat channel. Posting is not optional.

| Event | Who posts | What to post |
|-------|-----------|-------------|
| PR opened | PR author | Link + one line on what it does |
| PR merged | PR author | Link + what changed |
| Issue picked up | Assignee | Issue link + "starting work on this" |
| Issue completed | Assignee | Issue link + one line on outcome |
| Blocker hit | Anyone | What's blocked, why, what's needed |
| Key decision made | Decision owner | What was decided and why (link to issue/doc) |
| Saturday sync | Ajay & Sujal | Agenda posted Friday, notes posted Saturday after |

**Rules:**
- Keep it short — one to two lines max per update
- No skipping the Saturday sync — if you can't attend, post your update before it starts

---

## PR Description Format

```
Closes #<issue-number>

## What changed
One paragraph summary — what the code looked like before, what it looks like now.
Focus on WHY the change was needed, not just what was done.

## <Section per major change>
Each significant area gets its own heading.
Use before/after framing when it helps explain why.

## Code quality / correctness fixes  (if applicable)
Bullet list of smaller fixes bundled in.
Each bullet: what changed + why it matters.

## Future work landing cleanly on this structure  (if applicable)
Bullet list of issues this unblocks and where they now land.

## Acceptance criteria
- [x] Specific, testable condition
- [x] One per line
- [x] Covers the main behavior + edge cases
```
