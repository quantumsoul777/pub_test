---
name: save-progress
description: "Use when: saving session progress. Checks git status, writes or updates today's journal entry, updates features.md and other planning docs with current status, commits everything and pushes to current branch (stays on draft, never merges to main)."
---

You are saving session progress for this repository. Work through each step in order. Do not skip steps.

## Step 1 — Assess What Changed

Run `git status` and `git diff --stat HEAD` to identify what files changed this session. Read the recent conversation context to understand what was built, decided, or discussed.

## Step 2 — Update the Journal

Create or update `docs/02_history/[YYYYMMDD].md` using today's date. If the file already exists, append to it. The journal entry must include:
- What was built or changed (specific, factual — not vague summaries)
- Key decisions made and why
- Any open questions or blockers
- Immediate next steps

## Step 3 — Update Planning Documents

Check each of these and update only what needs updating:

- **`docs/03_planning/02_features.md`** — Update feature statuses based on what progressed:
  - All acceptance criteria checked + code complete → `Awaiting Merge`
  - Work started but not complete → `In Progress`
  - Do NOT mark anything `Complete` unless it has been merged to `main`
- **`docs/03_planning/01_roadmap.md`** — Reflect any direction changes or newly completed roadmap items
- **`docs/01_inputs/ideas.md`** — Add any new ideas surfaced in the session
- **`CHANGELOG.md`** — Add an entry if something significant shipped or changed

Do not make cosmetic edits. Only touch files that have real updates.

## Step 4 — Commit and Push

Stage all changes:
```
git add -A
```

Write a single commit message summarizing the session. Use the correct prefix:
- `feat:` — new functionality built
- `fix:` — bug fixed
- `docs:` — only documentation or planning changes
- `chore:` — maintenance, config, tooling
- `refactor:` — code restructured, no new behavior

If multiple types apply, use the most significant one.

Commit and push:
```
git commit -m "[your message]"
git push
```

**Stay on the current branch. Do NOT merge to main, switch branches, or reset anything.**

## Step 5 — Confirm

Report back concisely:
- Commit hash
- Which files were updated and what changed in each
- Current branch
- Any items still open before this branch is ready to merge
