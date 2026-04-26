---
name: dna-sync
description: "Use when: auditing or syncing a repo to DNA standards. Performs a thorough step-by-step check of DNA files, docs structure, planning documents, feature template compliance, and git hygiene. Flags issues, fixes what is safe to fix, and asks before touching anything with existing content."
---

You are performing a full DNA sync audit on this repository. Work through each step completely before moving to the next. Do not skip steps. Do not summarize steps you haven't done yet — execute them.

---

## Step 1 — Read the DNA

Read `_DNA.md` in full. Not skimming. The entire file.

Then confirm out loud: "I have read `_DNA.md` in full." State the `Last Updated` date from the file.

If `_DNA.md` does not exist in this repo, stop and report that. Do not proceed until it is propagated from zero-friction.

---

## Step 2 — Check Required DNA Files

Check whether each of these files exists in the repo:

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

Report a clear checklist — present (✅) or missing (❌) for each.

For any missing files: these must be propagated from zero-friction, not created here. Note them as **Action Required: propagate from zero-friction**.

---

## Step 2b — Does This Repo Actually Follow the DNA?

File presence is not compliance. Read the DNA rules and check whether this repo behaves accordingly. This step requires reading actual content — README, planning docs, commit history.

**Idea → Roadmap → Feature pipeline:**
- Are there features in `02_features.md` that have no corresponding roadmap entry? (skipped the roadmap stage)
- Are there items in `01_roadmap.md` that jumped there without going through `ideas.md` first? (can't verify retroactively, but if something appears fully detailed in the roadmap with no ideas entry, flag it)
- Are there TODO comments or half-built things in the codebase with no feature entry? If you can spot any, flag them.

**Commit hygiene:**
- Run `git log --oneline -20` and scan the last 20 commits.
- Flag any commits that don't use a valid prefix (`feat:`, `fix:`, `docs:`, `refactor:`, `chore:`).
- Flag any commits that look like they represent a full feature but have no corresponding feature entry.

**Lean File Rule:**
- Scan the repo for files that look speculative — empty files, placeholder files, files named "temp", "draft", "wip", "test", "old", or files with no content beyond a header.
- Flag each one with: what is it, when was it last modified, does anything reference it.

**Build Gate:**
- Check `docs/03_planning/02_features.md` for any feature marked `In Progress` that has no acceptance criteria, or where the criteria are all unchecked but significant code changes have been committed. This may indicate code was written before the feature was properly scoped.

Report findings. Flag for Pablo — do not auto-fix behavioral violations.

---

## Step 2c — Does This Repo Embody Phoenix Voice?

Read `_PHOENIX_VOICE.md` in full before doing this step.

Then read the repo's `README.md` and any content in `docs/00_foundation/` or `docs/05_knowledge/` that contains written prose (not just checklists or templates).

Check each of the following. For each violation, quote the offending text and suggest a fix:

**Lead with what IS:**
- Flag any sentence that opens with "not", "no", "don't", "never", "without", "this isn't" — these lead with what something is NOT before saying what it IS.

**No empty contrast:**
- Flag constructions like "you're not X, you're Y" or "this isn't just X, it's Y" where no one established X first.

**No hollow openers:**
- Flag phrases like "let's be clear", "the truth is", "it's important to note", "simply put" — they announce what's coming instead of just saying it.

**No hedging:**
- Flag "feels like", "seems to", "perhaps", "might be", "kind of", "sort of" in places where a direct statement was possible.

**No colons in prose:**
- Flag colons used mid-sentence in flowing prose (e.g., "The goal is clear: we need to..."). Colons in code blocks, lists, and tables are fine.

**No em dashes in prose:**
- Flag em dashes (`—`) used in prose sentences (not the `we are—` tagline and not markdown section headers). Rewrite suggestions: use a period, restructure the sentence.

**Inclusive language:**
- Flag places where "they", "the user", or "you should" distances the reader instead of using "we", "our", "us".

**Plain language:**
- Flag jargon or technical terms used in prose that a general audience would need specialized knowledge to understand.

**Genuine over performative:**
- Flag phrases that perform care or enthusiasm rather than expressing it: "we're excited to", "we're passionate about", "incredible", "amazing", "revolutionary", "game-changing".

This step applies to human-facing content. Code comments, YAML, and pure technical docs (schemas, API specs) are exempt.

---

## Step 2d — Does This Repo Reflect UNIVRSOL?

Read `_UNIVRSOL.md` in full before doing this step.

UNIVRSOL's position is: everyone belongs, no hierarchy, genuine care, plain language, the brand moves with humanity. Check whether this repo reflects that in how it presents itself.

**Is this repo described as part of UNIVRSOL?**
- Does the README or `docs/00_foundation/` acknowledge that this repo is part of UNIVRSOL? It doesn't need a manifesto — even one sentence is enough. If there's nothing, flag it.

**Does the tone reflect genuine care vs. transactional or corporate?**
- Read the README opening. Does it feel like it was written by a person who cares about the person reading it, or does it feel like documentation produced to satisfy a requirement?
- Flag any passage that feels bureaucratic, performative, or indifferent.

**Does it position itself above the reader?**
- Flag any language that talks down to the user, assumes they're a problem to be managed, or creates a hierarchy between "us" (the tool/project) and "them" (the user).

**Is it accessible?**
- Would someone with no prior context understand what this project is and why it exists within the first three sentences of the README?
- If no, flag what's missing.

Report findings as specific observations. This step requires judgment — flag for Pablo rather than auto-fixing.

---

## Step 3 — Check Docs Folder Structure

Check whether each of these directories exists:

- `docs/00_foundation/`
- `docs/01_inputs/`
- `docs/02_history/`
- `docs/03_planning/`
- `docs/04_creation/`
- `docs/05_knowledge/`
- `docs/09_archive/`

Report present (✅) or missing (❌) for each.

For any missing directories: create them now (with a `.gitkeep` file inside). This is safe — you are not overwriting anything.

---

## Step 4 — Check Planning Files

Check whether these files exist:

- `docs/03_planning/01_roadmap.md`
- `docs/03_planning/02_features.md`
- `docs/01_inputs/ideas.md`
- `CHANGELOG.md`
- `VERSION.txt`

For each missing file: create it with a minimal starter template. Use today's date. Include a comment noting it was created by dna-sync. The template for `02_features.md` must include the required section headers: `## In Progress`, `## Awaiting Merge`, `## Planned`.

For each existing file: read it and proceed to Step 5.

---

## Step 5 — Audit `02_features.md` for Template Compliance

Read `docs/03_planning/02_features.md` in full.

For every feature entry, verify it has ALL of the following fields:
- `**Status:**` — must be one of: `Planned`, `In Progress`, `Awaiting Merge`, `Complete`
- `**Target Version:**` — must use a version number (v0.x), never "Phase 1" or "Near-Term"
- `**Priority:**` — must be `High`, `Medium`, or `Low`
- `**Description:**` — must be present and non-empty
- `**Why:**` — must be present and non-empty
- `**Acceptance Criteria:**` — must have at least one item

Also check for:
- Crossed-out / strikethrough text (not allowed — archive or delete)
- Features with all criteria checked `[x]` but status still `In Progress` (should be `Awaiting Merge`)
- Phase-based language ("Phase 1", "Near-Term", "Future") — replace with version numbers
- Stale historical notes that belong in `docs/02_history/` instead

Report every issue found. For each:
- Issues that are clearly a data entry problem (wrong status when all criteria are checked, phase language) → fix them now
- Issues that require judgment (missing Why, vague descriptions) → flag for Pablo with a specific question

---

## Step 6 — Audit `01_roadmap.md`

Read `docs/03_planning/01_roadmap.md` in full.

Check for:
- Crossed-out / strikethrough items (not allowed — archive or delete)
- Phase-based version labels ("Phase 1") — replace with version numbers
- Items that have been built but are not marked complete (✅)

Fix what's clear. Flag what needs judgment.

---

## Step 7 — Git Hygiene Check

Run `git status` and report:
- Current branch
- Uncommitted changes (list files)
- Untracked files worth noting

Do NOT commit anything during this step. This is read-only. If there are uncommitted changes, flag them and ask Pablo how to handle.

---

## Step 8 — Final Report

Produce a structured summary:

```
### DNA Sync Report — [repo name] — [date]

**DNA Files:** X/9 present
**DNA Behavioral Compliance:** [list any violations — skipped pipeline stages, commit hygiene, speculative files]
**Phoenix Voice:** [list violations with quoted text and suggested fixes, or ✅ Clean]
**UNIVRSOL Alignment:** [list observations, or ✅ Clean]
**Docs Structure:** X/7 dirs present
**Planning Files:** [list status of each]
**Features Audited:** X entries
**Issues Fixed:** [list]
**Issues Flagged for Pablo:** [list with specific questions]
**Git Status:** [branch, clean/dirty]
```

Then ask: "Shall I commit the fixes made during this sync?"

If yes: stage only the files changed during this sync and commit with message: `chore: DNA sync audit — [brief description of what was fixed]`
