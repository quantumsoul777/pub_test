---
name: docs-health
description: "Use when: checking that docs are internally consistent, accurate, and current. Checks feature statuses, cross-references, links, VERSION/CHANGELOG sync, redundancy, and planning pipeline drift. Run after every major task or feature update. Lightweight — docs only, no code changes."
---

You are performing a docs health check on this repository. This is not a full structural audit — that's `/dna-sync`. This is a focused check that the documentation accurately reflects the current state of the project, is internally consistent, and has no drift or redundancy.

Work through each step completely. Do not skip. Do not fix anything in code. Docs only.

---

## Step 1 — Read Planning State

Read all three of these files in full before doing anything else:

1. `docs/03_planning/02_features.md`
2. `docs/03_planning/01_roadmap.md`
3. `docs/01_inputs/ideas.md`

Confirm you have read all three. Do not proceed until you have.

---

## Step 2 — Feature Status Accuracy

For every entry in `02_features.md`, check:

**Status drift:**
- All `[x]` acceptance criteria + status is `In Progress` → should be `Awaiting Merge`. Fix it.
- All `[x]` acceptance criteria + status is `Awaiting Merge` + is on `main` branch → should be `Complete`. Flag for Pablo — do not auto-flip without confirmation.
- Status says `Complete` but entry is still in the active file (not archived) → flag. Ask Pablo to confirm it should move to `docs/09_archive/completed-features.md`.

**Template compliance:**
- Missing `**Why:**`, `**Priority:**`, or `**Acceptance Criteria:**` → flag with the feature name and what's missing
- Phase language anywhere ("Phase 1", "Near-Term", "Future Enhancements") → fix to version numbers
- Crossed-out / strikethrough text → flag. Ask Pablo: archive or delete?

**Redundancy:**
- Same feature appearing more than once (exact or near-duplicate) → flag both instances

---

## Step 3 — Roadmap Accuracy

Read `01_roadmap.md` and check:

- Items marked `✅` that still have a corresponding active feature entry in `02_features.md` → the feature entry should also be `Complete` or archived. Flag if it isn't.
- Items NOT marked `✅` that DO have a `Complete` or `Awaiting Merge` feature → roadmap item should be updated. Fix it.
- Any item using phase language → fix to version numbers
- Any crossed-out items → flag for archive or deletion
- Roadmap version sections with no items → flag as potentially stale

---

## Step 4 — Ideas Pipeline Check

Read `ideas.md` and check:

- Ideas that have a corresponding entry in `02_features.md` or `01_roadmap.md` → the idea was promoted but may still be sitting in ideas. Flag: "This idea appears to have been promoted. Should it be removed from ideas.md?"
- Ideas marked with any kind of status label that implies a decision was made (e.g., "building this", "in progress") → they should have been promoted out of ideas already. Flag.
- Do NOT remove ideas automatically. Always ask.

---

## Step 5 — VERSION and CHANGELOG Sync

Read `VERSION.txt` and `CHANGELOG.md`.

Check:
- Does the version in `VERSION.txt` match the most recent version heading in `CHANGELOG.md`?
- Does `CHANGELOG.md` have an entry for the current version?
- If features are `Awaiting Merge` or `Complete` for a version but `CHANGELOG.md` has no entry for that version → flag: "These features are done for vX.X but CHANGELOG.md has no entry for it."

Report the current version and last changelog entry date.

---

## Step 6 — Cross-Reference Integrity

Scan the docs for internal links and references. Check:

- Markdown links (`[text](path)`) — does the target file or section exist?
- References to specific files by name (e.g., "`_DNA.md`", "`docs/03_planning/02_features.md`") — do those files exist?
- References to version numbers (e.g., "see v1.2") — does that version section exist in the roadmap?

Report every broken or unresolvable reference. Do not auto-fix — flag for Pablo.

---

## Step 6b — Terminology Drift

Scan all docs files for outdated terminology:

- Old folder names that no longer exist (e.g., `docs/00_project_context/`, `docs/02_current_state/`, `scaffolds/`)
- Renamed commands or scripts (e.g., references to scripts that have been renamed or moved)
- Deprecated file names (e.g., `ai_context.md`, `.copilot_context.md`)
- Any references to "Phase 1 / Phase 2" language

Flag each occurrence with file name, line context, and suggested replacement. Do not auto-fix.

---

## Step 6c — File Header Date Accuracy

Every markdown file in this repo that has a `<sub>**Modified:** YYYY-MM-DD</sub>` header should reflect when it was last meaningfully changed.

Run `git log --format="%ad" --date=short -1 -- <file>` for each doc file with a Modified header.

Compare the header date against the git last-modified date. Flag any file where the header date is more than 7 days older than the actual last-modified date in git — these headers have drifted.

Do not auto-fix. Report the file, the header date, and the actual git date.

---

## Step 7 — Journal Gap Check

List the files in `docs/02_history/` and identify the most recent entry.

Then consider: based on the current state of `02_features.md` (features marked `Awaiting Merge`, criteria recently checked, etc.), does it look like meaningful work has happened since the last journal entry?

If yes, and there's no recent journal entry: flag — "Significant work appears to have happened since [last journal date]. Consider running `/save-progress` to write a journal entry."

Do not create a journal entry here. That's `/save-progress`'s job.

---

## Step 8 — Redundancy and Noise Check

Scan the docs folder (not code) and check for:

- Files in `docs/` that are not referenced by anything and whose names don't match expected patterns — flag as potentially orphaned
- Duplicate information (same decision, same feature description, same note) appearing in multiple files — flag the locations
- Files in `docs/03_planning/` that are not `01_roadmap.md`, `02_features.md`, or `03_issues.md` — these may be misplaced feature specs that should be in `docs/04_creation/`

---

## Step 9 — Final Report

Produce a structured summary:

```
### Docs Health Report — [repo name] — [date]

**Feature Status Issues:** [count] — [list]
**Roadmap Drift:** [count] — [list]
**Ideas Pipeline Flags:** [count] — [list]
**VERSION/CHANGELOG Sync:** [OK or issue]
**Broken Cross-References:** [count] — [list]
**Journal Gap:** [OK or flag]
**Redundancy/Noise:** [count] — [list]

**Auto-fixed:** [list anything that was changed without asking]
**Needs Pablo's decision:** [list with specific yes/no questions]
```

Then ask: "Shall I commit the fixes made during this check?"

If yes: commit only the files changed during this check with message: `docs: Docs health check — [brief summary of fixes]`
