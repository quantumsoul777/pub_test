---
name: repo-check
description: "Use when: you want a complete audit of this repo — structure, compliance, content accuracy, and docs health in one pass. Combines dna-sync and docs-health. Run when entering a repo after time away, before a merge, or whenever you want the full picture."
---

You are performing a complete repository audit. This combines a full DNA sync check with a docs health check. Work through every step in order. Do not skip. Do not summarize steps you haven't done yet — execute them.

---

# PART 1 — DNA SYNC
## Structure, compliance, voice, and cultural alignment

---

## Step 1 — Read the DNA

Read `_DNA.md` in full. The entire file. Not skimming.

Confirm: "I have read `_DNA.md` in full." State the `Last Updated` date.

If `_DNA.md` does not exist, stop. Report it and do not proceed until it is propagated from zero-friction.

---

## Step 2 — Required DNA Files

Check whether each file exists:

| File | Required |
|------|----------|
| `_DNA.md` | Yes |
| `_UNIVRSOL.md` | Yes |
| `_PHOENIX_VOICE.md` | Yes |
| `CLAUDE.md` | Yes |
| `AGENTS.md` | Yes |
| `.github/copilot-instructions.md` | Yes |
| `.github/workflows/dna-callback.yml` | Yes |
| `.github/prompts/save-progress.prompt.md` | Yes |
| `.github/prompts/dna-sync.prompt.md` | Yes |
| `.github/prompts/docs-health.prompt.md` | Yes |
| `.github/prompts/repo-check.prompt.md` | Yes |
| `.github/prompts/save-progress-merge.prompt.md` | Yes |

Report present (✅) or missing (❌). Missing files must be propagated from zero-friction — do not create them here.

---

## Step 3 — DNA Behavioral Compliance

File presence is not compliance. Check whether this repo actually follows the DNA rules.

**Idea → Roadmap → Feature pipeline:**
- Features in `02_features.md` with no corresponding roadmap entry — flag (skipped the roadmap stage)
- TODO comments or half-built code with no feature entry — flag if you can spot any

**Commit hygiene:**
- Run `git log --oneline -20` and scan the last 20 commits
- Flag any commits missing a valid prefix (`feat:`, `fix:`, `docs:`, `refactor:`, `chore:`)

**Lean File Rule:**
- Scan for speculative files: empty, placeholder, or named "temp", "draft", "wip", "old"
- Flag each with: what is it, last modified date, does anything reference it

**Build Gate:**
- Flag any feature marked `In Progress` with no acceptance criteria — may indicate code written before the feature was scoped

Flag for Pablo. Do not auto-fix behavioral violations.

---

## Step 4 — Phoenix Voice Check

Read `_PHOENIX_VOICE.md` in full before this step.

Read the repo's `README.md` and any prose in `docs/00_foundation/` or `docs/05_knowledge/`. For each violation, quote the text and suggest a fix.

- **Lead with what IS** — flag sentences opening with "not", "no", "don't", "never", "without", "this isn't"
- **No empty contrast** — flag "you're not X, you're Y" or "this isn't just X, it's Y" where X was never established
- **No hollow openers** — flag "let's be clear", "the truth is", "it's important to note", "simply put"
- **No hedging** — flag "feels like", "seems to", "perhaps", "might be", "kind of", "sort of" where a direct statement was possible
- **No colons in prose** — flag colons mid-sentence in flowing prose (code blocks, lists, tables exempt)
- **No em dashes in prose** — flag `—` in prose sentences (section headers and `we are—` tagline exempt)
- **Inclusive language** — flag "they", "the user", "you should" where "we", "our", "us" belongs
- **Plain language** — flag jargon a general audience would need specialized knowledge to understand
- **Genuine over performative** — flag "we're excited to", "incredible", "amazing", "revolutionary", "game-changing"

Applies to human-facing content only. Code comments, YAML, and pure technical docs are exempt.

---

## Step 5 — UNIVRSOL Alignment

Read `_UNIVRSOL.md` in full before this step.

- **Is this repo described as part of UNIVRSOL?** — README or `docs/00_foundation/` should acknowledge it, even one sentence. Flag if absent.
- **Tone** — Does the README opening feel written by a person who cares, or documentation produced to satisfy a requirement? Flag bureaucratic or indifferent passages.
- **Hierarchy** — Flag language that talks down to the user or positions the project above the reader.
- **Accessibility** — Would someone with no prior context understand what this project is and why it exists within the first three sentences? Flag if not.

Flag for Pablo. This step requires judgment — do not auto-fix.

---

## Step 6 — Docs Folder Structure

Check whether each directory exists:

- `docs/00_foundation/`
- `docs/01_inputs/`
- `docs/02_history/`
- `docs/03_planning/`
- `docs/04_creation/`
- `docs/05_knowledge/`
- `docs/09_archive/`

Report present (✅) or missing (❌). For any missing: create them now with a `.gitkeep` inside. This is safe.

---

## Step 7 — Planning Files Exist

Check whether these files exist:

- `docs/03_planning/01_roadmap.md`
- `docs/03_planning/02_features.md`
- `docs/01_inputs/ideas.md`
- `CHANGELOG.md`
- `VERSION.txt`

For any missing: create with a minimal starter template and a comment noting it was created by repo-check. The `02_features.md` template must include `## In Progress`, `## Awaiting Merge`, `## Planned` section headers.

---

# PART 2 — DOCS HEALTH
## Content accuracy, drift, and internal consistency

---

## Step 8 — Feature Status Accuracy

Read `docs/03_planning/02_features.md` in full.

**Template compliance** — every entry must have: `**Status:**`, `**Target Version:**`, `**Priority:**`, `**Description:**`, `**Why:**`, `**Acceptance Criteria:**`. Flag anything missing.

**Status drift:**
- All `[x]` criteria + status `In Progress` → fix to `Awaiting Merge`
- All `[x]` criteria + status `Awaiting Merge` + currently on `main` → flag for Pablo to confirm `Complete`
- Status `Complete` but still in active file (not archived) → flag for Pablo to confirm archival

**Other issues:**
- Phase language ("Phase 1", "Near-Term") → fix to version numbers
- Crossed-out / strikethrough text → flag: archive or delete?
- Duplicate feature entries → flag both instances

---

## Step 9 — Roadmap Accuracy

Read `docs/03_planning/01_roadmap.md` in full.

- Items `✅` that still have an active (non-Complete) feature entry → flag mismatch
- Items not `✅` that have a `Complete` or `Awaiting Merge` feature → fix the roadmap item
- Phase language → fix to version numbers
- Crossed-out items → flag for archive or deletion
- Version sections with no items → flag as potentially stale

---

## Step 10 — Ideas Pipeline Check

Read `docs/01_inputs/ideas.md` in full.

- Ideas with a corresponding entry in `02_features.md` or `01_roadmap.md` → flag as potentially promotable out of ideas. Ask Pablo before removing.
- Ideas with status labels implying a decision ("building this", "in progress") → should have been promoted already. Flag.

Do NOT remove ideas automatically.

---

## Step 11 — VERSION and CHANGELOG Sync

Read `VERSION.txt` and `CHANGELOG.md`.

- Does `VERSION.txt` use the `v` prefix (e.g., `v1.0.0`)? If not, fix it.
- Does the version in `VERSION.txt` match the most recent version heading in `CHANGELOG.md`?
- Features `Awaiting Merge` or `Complete` for a version with no `CHANGELOG.md` entry → flag: "These features are done for vX.X but CHANGELOG has no entry."

Report current version and last changelog entry date.

---

## Step 12 — Cross-Reference Integrity

Scan docs for internal links and references:

- Markdown links `[text](path)` — does the target exist?
- File name references (e.g., "`_DNA.md`") — does that file exist?
- Version references ("see v1.2") — does that section exist in the roadmap?

Flag every broken reference. Do not auto-fix.

---

## Step 13 — Terminology Drift

Scan all docs for outdated terminology:

- Old folder names that no longer exist (e.g., `docs/00_project_context/`, `docs/02_current_state/`, `scaffolds/`)
- Renamed scripts or commands
- Deprecated file names (e.g., `ai_context.md`, `.copilot_context.md`)
- Phase language anywhere in docs

Flag with file name, line context, and suggested replacement.

---

## Step 14 — File Header Date Accuracy

For each markdown file with a `<sub>**Modified:** YYYY-MM-DD</sub>` header, run:
```
git log --format="%ad" --date=short -1 -- <file>
```

Flag any file where the header date is more than 7 days older than the actual git last-modified date. Report: file name, header date, actual git date.

---

## Step 15 — Journal Gap Check

List files in `docs/02_history/` and identify the most recent entry.

If features are `Awaiting Merge` or criteria have been recently checked, meaningful work has likely happened. If there's no journal entry since that work: flag — "Significant work appears to have happened since [last journal date]. Consider running `/save-progress`."

Do not create a journal entry here.

---

## Step 16 — Redundancy and Noise

Scan `docs/` (not code) for:

- Files not referenced by anything with names outside expected patterns → flag as potentially orphaned
- Duplicate information appearing in multiple files → flag locations
- Files in `docs/03_planning/` other than `01_roadmap.md`, `02_features.md`, `03_issues.md` → may be misplaced specs, should be in `docs/04_creation/`

---

## Step 17 — Git Hygiene

Run `git status` and report:
- Current branch
- Uncommitted changes (list files)
- Untracked files worth noting

Read-only. Do not commit. If uncommitted changes exist, flag and ask Pablo how to handle.

---

## Step 18 — Final Report

```
### Repo Check Report — [repo name] — [date]

PART 1 — DNA SYNC
**DNA Files:** X/12 present — [list any missing]
**Behavioral Compliance:** [list violations, or ✅ Clean]
**Phoenix Voice:** [list violations with quoted text, or ✅ Clean]
**UNIVRSOL Alignment:** [list observations, or ✅ Clean]
**Docs Structure:** X/7 dirs present
**Planning Files:** [list status of each]

PART 2 — DOCS HEALTH
**Feature Status Issues:** [count] — [list]
**Roadmap Drift:** [count] — [list]
**Ideas Pipeline Flags:** [count] — [list]
**VERSION/CHANGELOG Sync:** [OK or issue]
**Broken Cross-References:** [count] — [list]
**Terminology Drift:** [count] — [list]
**File Header Dates:** [count drifted] — [list]
**Journal Gap:** [OK or flag]
**Redundancy/Noise:** [count] — [list]
**Git Status:** [branch, clean/dirty]

**Auto-fixed:** [list anything changed without asking]
**Needs Pablo's decision:** [numbered list with specific yes/no questions]
```

Then ask: "Shall I commit the fixes made during this check?"

If yes: commit only files changed during this check with message: `docs: Repo check — [brief summary of fixes]`
