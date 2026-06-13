# Contributing to Alumni Connect

## 1. Prerequisites

- Git installed locally
- Clone the repo: `git clone https://github.com/ColoredCow/alumni-connect.git`
- Join the `#alumni-connect` Google Chat channel — all project communication happens there

## 2. Understanding the Project

Before picking up any work:

- Read [`docs/architecture.md`](docs/architecture.md) — understand the problem, target users, and V1 scope
- Check the [Kanban board](https://github.com/orgs/ColoredCow/projects/61) — see what's in progress, what's ready to pick up
- Read [`docs/communication-process.md`](docs/communication-process.md) — understand how the team communicates

## 3. Picking Up Work

1. Find an issue in the **To Do** column on the Kanban board
2. Assign yourself to the issue on GitHub
3. Move the card to **In Progress**
4. Post in `#alumni-connect`: issue link + "starting work on this"

Don't start work without an issue. If something needs doing and there's no issue, create one first.

## 4. Making Changes

**Branch naming:**
```
feat/<short-description>        # new feature or addition
fix/<short-description>         # bug fix
docs/<short-description>        # documentation only
chore/<short-description>       # config, tooling, cleanup
```

**Commit message style:**
- One short line describing what changed and why
- No "WIP", no "misc changes", no "updated file"
- Example: `Add alumni profile schema to architecture doc`

## 5. Opening a PR

Link the PR to the issue it closes. Use this format:

```
Closes #<issue-number>

## What changed
One paragraph summary — what it looked like before, what it looks like now.
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

Post in `#alumni-connect` when the PR is open: link + one line on what it does.

## 6. After the PR

- A reviewer will be assigned — don't merge your own PR
- If there are review comments, push fixes and reply on the thread — don't resolve threads yourself
- Once approved, the reviewer or Ajay merges
- Post in `#alumni-connect` when merged: link + one line on what changed
- Move the Kanban card to **Done**
