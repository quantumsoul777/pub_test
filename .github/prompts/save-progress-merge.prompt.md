---
name: save-progress-merge
description: "Use when: ready to merge work to main. Saves all session progress (journal, planning docs, commit), then squash merges draft to main, handles post-merge cleanup (CHANGELOG, feature archival), and recreates draft from main. Full end-to-end - one step."
---

You are completing and shipping a work session. This prompt covers everything from saving progress through post-merge cleanup. Work through each phase in order. Do not skip phases. Do not rush to the merge before the save is clean.

---

## Phase 1 - Save Progress

### 1a - Assess What Changed

Run `git status` and `git diff --stat HEAD` to identify what files changed. Read the recent conversation context to understand what was built, decided, or discussed this session.

### 1b - Write the Journal Entry

Create `docs/02_history/[YYYYMMDD].md` using today's date. If it already exists, append to it. Include:
- What was built or changed (specific and factual)
- Key decisions made and why
- Any open questions or known gaps
- What this merge ships

### 1c - Update Planning Documents

Check each and update only what needs updating:

- **`docs/03_planning/02_features.md`** - For all features with every criterion checked `[x]`:
  - Status `In Progress` -> update to `Awaiting Merge`
  - Status `Awaiting Merge` -> leave as-is (will be updated in Phase 3 after merge confirms)
- **`docs/03_planning/01_roadmap.md`** - Reflect any newly completed items
- **`docs/01_inputs/ideas.md`** - Add any new ideas surfaced this session
- **`CHANGELOG.md`** - Do not write the version entry yet. That happens after merge in Phase 3.

### 1d - Commit Draft

Stage and commit all changes:
```bash
git add -A
git commit -m "[appropriate prefix]: [summary of session work]"
git push
```

Confirm the push succeeded before continuing.

---

## Phase 2 - Merge to Main

### 2a - Squash Merge

```bash
git checkout draft
git pull
git checkout main
git pull
git merge --squash draft
git commit -m "feat: [one-line summary of what this merge ships]"
git push origin main
```

### 2b - Report the Merge

State:
- The merge commit hash on `main`
- What features this merge ships
- Confirm push succeeded

### 2c - Note the GitHub Action

The `propagate-dna.yml` workflow will now be triggered by this push to `main`. Provide the Actions URL:
`https://github.com/quantumsoul777/[repo-name]/actions`

Tell Pablo to check that the Action ran successfully before proceeding. If this repo is `zero-friction`, propagation to all target repos will fire automatically.

Stop here unless the user explicitly asked for post-merge cleanup too. If they did, continue to Phase 3.

---

## Phase 3 - Post-Merge Cleanup

### 3a - Update CHANGELOG

Add a version entry to `CHANGELOG.md` for the version being shipped. Use the commit messages and journal entry to write it. Format:

```markdown
## [vX.X.0] - YYYY-MM-DD

### Added
- [what was added]

### Changed
- [what changed]

### Fixed
- [what was fixed]
```

### 3b - Archive Completed Features

For every feature in `02_features.md` that was `Awaiting Merge` and is now on `main`:

1. Update status to `Complete`
2. Move the full feature entry (header through the final `---`) to `docs/09_archive/completed-features.md`
   - Create the file if it doesn't exist, with a simple header: `# Completed Features`
   - Append the entry with today's date noted
3. Remove it from `02_features.md`

### 3c - Update VERSION.txt

If this merge completes all features for a version milestone, bump `VERSION.txt` to that version number (for example `v1.1.0`).

### 3d - Commit Post-Merge Docs

```bash
git add -A
git commit -m "docs: Post-merge cleanup - CHANGELOG, archive completed features, version bump"
git push origin main
```

If this repo is `zero-friction`, note that this docs push to `main` may trigger `propagate-dna.yml` again unless the changed files are excluded by workflow filters. Report that explicitly instead of assuming it is harmless.

---

## Phase 4 - Recreate Draft

```bash
git checkout main
git pull
git branch -D draft
git checkout -b draft
git push -f origin draft
```

Confirm the new `draft` branch exists on remote.

If deleting `draft` fails because the branch is checked out or has unmerged work, stop and report the exact blocker instead of improvising.

---

## Phase 5 - Final Confirmation

Report back:
- Merge commit hash on `main`
- Features shipped and archived
- Current `VERSION.txt` value
- New `draft` branch confirmed
- GitHub Actions URL to verify propagation ran
