<sub>**File:** _DNA.md</sub>  
<sub>**Created:** 2026-02-07</sub>  
<sub>**Modified:** 2026-02-24</sub>  
<sub>**Purpose:** Universal DNA - Pablo's work patterns, structure rules, and AI behavior across ALL projects</sub>
   
---
# _DNA - Universal Work Patterns

> **This file is the source of truth for all projects and all agents.** Read it in full before acting. Any additions to this file must follow Phoenix Voice (`_PHOENIX_VOICE.md`) for tone and clarity. The DNA speaks the same way UNIVRSOL does — plainly, directly, with genuine care for the person reading it.

## Return to Source

You have no memory of yesterday. That's fine — this file is your memory.

Every time you open a project, every time a new session starts, every time you feel lost or unsure what to do next — come back here. This file tells you who you're working with, how they work, what they're building, and how they expect you to show up. Read it in full before doing anything else. Not skimming — reading. The structure here is intentional and every part of it matters.

Who you're working with: Pablo — a builder who moves fast, values structure, hates bloat, and needs to trust that you know what you're doing and will tell him what you're doing.

**Last Updated:** 2026-04-26

---

## AI AGENT ENFORCEMENT RULES

**These rules apply to ALL AI agents — GitHub Copilot, Claude, Codex, GPT, or any other.**  
**No agent is exempt. No project is exempt. This is not optional.**

### What Every AI Agent MUST Do

1. **Read this file in full before taking any action.** Not skimming — reading. The structure here is intentional and must be followed.

2. **Enforce the Idea → Roadmap → Feature pipeline.** Do not add items to features without the full template. Do not add items to the roadmap that belong in ideas. Do not blur the lines between these three stages.

3. **Use version numbers, not phases.** Never write "Phase 1", "Phase 2", "Phase 3", "Near-Term", or "Future Enhancements" in planning documents. Use version numbers: `v0.1`, `v0.2`, `v1.0`.

4. **Use the required feature template.** No incomplete feature entries. If you can't fill out the template, the feature isn't ready to be a feature yet — put it in the roadmap or ideas instead.

5. **Do not leave crossed-out text in active planning files.** Completed or abandoned items either move to `09_archive/` or get deleted. Strikethrough in `01_roadmap.md` or `02_features.md` is not allowed.

6. **Keep planning files clean.** Historical notes, stale context, and "SUPERSEDED" blocks do not belong in `01_roadmap.md` or `02_features.md`. Those go in `02_history/` entries.

7. **Journal sessions.** If meaningful work was done, create a session log at `docs/02_history/YYYYMMDD.md`. Do not skip this step when asked to commit and journal.

8. **Commit with clear, consistent messages.** Follow the prefix conventions: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`. One commit per logical change.

### The Build Gate — MANDATORY

**Before writing any code, the following must exist and be approved by the user:**

1. A feature entry in `02_features.md` using the required template
2. The user has confirmed: "Yes, build this"

**If these conditions are not met, do NOT start coding. Instead:**
- Write the feature entry
- Show it to the user
- Wait for explicit approval

A conversation is not approval. Enthusiasm is not approval. "Sounds good" is not approval.  
**Approval = the user says to build it after reading the feature spec.**

---

### The Lean File Rule — MANDATORY

**Do not create files speculatively.** Only create a file when:
- It has content to put in it right now
- It will be actively used (not just referenced)
- The user asked for it

**Do NOT create files because:**
- "It might be useful later"
- "This is part of the standard structure"
- You want to show thoroughness

Empty files, placeholder files, and files created "just in case" are noise. They create the illusion of organization while making the repo harder to navigate. If a folder only has `.gitkeep` files with no real content, that is fine — it means the project hasn't needed that folder yet.

**The test:** If a file was created more than a session ago and has never been read or updated, it should not exist.

---

### One Feature File Rule — MANDATORY

**All features live as entries inside `docs/03_planning/02_features.md`. Do not create a separate file per feature.**

❌ `docs/03_planning/05_ai_profile_generator.md` — wrong  
✅ A `### AI Profile Generator` section inside `02_features.md` — correct

**Why:** Separate feature files fragment visibility. The whole point of `02_features.md` is that it is the single place to see what's being built, what's in progress, and what's done. Splitting features into individual files breaks that.

**The only exception:** A feature is so large it needs a full design doc — architecture diagrams, API contracts, data models, open questions. In that case:
1. The entry still exists in `02_features.md` (with status, version, acceptance criteria)
2. A separate spec file lives in `docs/04_creation/` (not in `03_planning/`)
3. The feature entry in `02_features.md` links to it: `**Spec:** [04_creation/my-feature-spec.md]`

If you're not sure whether a feature is large enough to warrant a spec file — it isn't. Use the template in `02_features.md` and move on.

---

### What AI Agents Must NOT Do

- Write code without a feature entry and explicit user approval
- Create files speculatively or "for structure"
- Add features without the required template
- Use phase-based language in planning docs
- Create new doc structures outside the `docs/00-09` framework
- Modify `_DNA.md` in any project other than `zero-friction`
- Leave stale, crossed-out, or "SUPERSEDED" content in active planning files
- Skip the journal/commit step when the user asks to save progress
- Assume vague instructions mean freedom to invent structure

### If Instructions Are Unclear or Missing
Ask the user. Do not invent structure. Do not make assumptions. The DNA exists so you don't have to guess — if something isn't covered here, ask before acting.

---

## Universal Agent Files

Every project contains four files that together ensure any AI agent reads the DNA before acting. These are propagated from zero-friction via `scripts/propagate_dna.py`.

| File | Read by | Purpose |
|------|---------|---------|
| `_DNA.md` | All agents (by instruction) | Full rules — the source of truth |
| `CLAUDE.md` | Claude Code (auto-loaded at startup) | Gateway → `_DNA.md` |
| `AGENTS.md` | Codex CLI and open-standard agents | Gateway → `_DNA.md` |
| `.github/copilot-instructions.md` | GitHub Copilot (auto-loaded in VS Code) | Gateway → `_DNA.md` |
| `.github/workflows/dna-callback.yml` | GitHub Actions (in all repos) | Sends push events back to zero-friction |

**CLAUDE.md, AGENTS.md, and copilot-instructions.md are thin.** They contain the critical TL;DR rules and a single instruction: read `_DNA.md`. They do not duplicate the full DNA — they point to it.

Two additional files belong in every project and are also propagated:

| File | Purpose |
|------|---------|
| `_UNIVRSOL.md` | What UNIVRSOL is — the mission, the people, the position we hold |
| `_PHOENIX_VOICE.md` | The writing standard for all UNIVRSOL content — Part 1 (Writer/Drafter) + Part 2 (Editor/QC) |

All repos are UNIVRSOL. There are no exceptions. Read both files before writing any content.

**To propagate to all repos after updating DNA:**
```powershell
cd d:\repos\zero-friction
python scripts/propagate_dna.py
```

---

## The Resync Command

**If you feel an agent is drifting, not being transparent, or building without a plan — say this:**

> **"DNA sync"**

When an agent receives this command, it MUST immediately stop whatever it is doing and respond with the following, in order:

### 1. Confirm DNA is loaded
State: "I have read `_DNA.md` in full."  
If it hasn't been read this session, read it now before continuing.

### 2. Report current state
Answer each of these:
- What feature(s) are currently `In Progress` in `docs/03_planning/02_features.md`?
- What was the last thing built or changed in this session?
- What files were created or modified this session, and why?

### 3. Surface anything unscoped
List any work done or planned that does NOT have a corresponding feature entry in `02_features.md`. For each item: was it explicitly approved, or was it assumed?

### 4. State the next action
One sentence: what is the very next thing the agent intends to do, and which feature entry in `02_features.md` authorizes it?

### 5. Ask for confirmation before continuing
Do not resume work until the user says to proceed.

---

**This command exists because:** AI agents can drift — creating files, making decisions, and building things without the user having a clear picture of what's happening. "DNA sync" is a hard stop that forces transparency. Use it any time you feel out of the loop.

**You can also say:**
- **"What are you building?"** — Agent must cite the feature entry authorizing the current work
- **"Show me what you've created this session"** — Agent must list every file created/modified with a one-line reason for each
- **"Is this in the feature spec?"** — Agent must answer yes/no and cite the specific acceptance criteria, or admit it was not scoped

---

**THIS IS A FRESHLY SCAFFOLDED PROJECT**

This folder was cloned from the zero-friction scaffold template. Here's what you need to know:

### What to Keep (Universal Structure)
- `docs/` folder structure (language-agnostic)
- `VERSION.txt` and `CHANGELOG.md`
- This `_DNA.md` file
- `.gitignore` patterns

### What to Replace (Language-Specific Placeholders)
- **Entry Point**: `src/main.py` is a PLACEHOLDER
  - Python projects: Keep it
  - JavaScript/Node: Replace with `index.js` or `app.js`
  - React: Replace with `App.jsx` or `index.jsx`
  - Rust: Replace with `main.rs`
  - etc.
  
- **Dependency File**: `requirements.txt` is a PLACEHOLDER
  - Python: Keep it (or use `pyproject.toml`, `environment.yml`)
  - JavaScript: Replace with `package.json`
  - Rust: Replace with `Cargo.toml`
  - etc.

**The scaffold creator codes mostly in Python**, so main.py is the default placeholder. Swap it for whatever your language uses! The docs structure, VERSION.txt, CHANGELOG.md, and _DNA.md work for ANY project type.

---

## IMPORTANT: _DNA.md is Read-Only in Projects

**This file is only updated in zero-friction, then propagated to other projects.**

**When working in project repos:**
- **DO NOT** modify _DNA.md
- **DO** read and follow it
- **DO** document project-specific patterns in `docs/05_knowledge/`

**When you learn something universal (applies to ALL projects):**
- Document it in zero-friction's _DNA.md
- Propagate the updated DNA to other projects
- For now, this is manual - future automation may handle it

**_DNA.md is immutable outside zero-friction.**

---

## PRINCIPLES OVER RULES

**This DNA teaches WHY, not WHAT EXACTLY.**

Every project is different. Your Python project might have `alembic/` for database migrations. Your Node project has `node_modules/`. Your app might need `uploads/` or `cache/` directories. **This is expected and fine.**

**The DNA provides:**
- **Core philosophy** - Why things go where they go
- **Universal patterns** - Docs for thinking, src for doing, root for running
- **Self-audit questions** - How to decide when the DNA doesn't prescribe

**The DNA does NOT provide:**
- Exhaustive rules for every framework
- Rigid enforcement of exact structure
- Prescriptions that ignore your domain needs

**When your project doesn't match the DNA exactly:**
1. Ask: "Does this violate the core principle?" (Docs = knowledge, src = code, root = running)
2. Ask: "Is this standard for my framework/language?"
3. Ask: "Would someone cloning this understand it in 30 seconds?"

**If the answers are: No violation, Yes it's standard, Yes it's clear** → You're fine. Document it and move on.

**The goal:** Clarity and consistency, not rigidity.

---

## QUICK REFERENCE: Where Does It Go?

**BEFORE asking where something belongs, check this decision tree:**

### 🧠 Raw Idea or Thought?
→ **`docs/01_inputs/ideas.md`**
- Unfiltered brain dumps
- "What if we..." thoughts
- Random inspirations
- No commitment needed, just capture it

### 📥 External Request or Feedback?
→ **`docs/01_inputs/requests.md`**
- Customer feature requests
- User feedback
- Collaboration opportunities
- Things people asked for

### 🐛 Bug or Problem?
→ **GitHub Issues** (if using issue tracking)
→ **`docs/03_planning/04_issues.md`** (if tracking in docs)
- Something broken
- Technical debt to fix
- Known limitations causing problems

### 📋 Decided It's Worth Building?
→ **`docs/03_planning/01_roadmap.md`** (directional intent, version target, brief description)
- You've decided it's worth doing but haven't fully scoped it yet
- Add it to the roadmap under the appropriate target version
- Do NOT put it directly in features until you're ready to write the full template

### 🔧 Scoping or Starting to Build?
→ **`docs/03_planning/02_features.md`** (full feature template required)
- Use the mandatory feature template: Status, Version, Priority, Description, Why, Acceptance Criteria
- No shortcuts — incomplete entries are not valid features

### 📚 Reference, Research, or Architecture?
→ **`docs/05_knowledge/`**
- How the system works
- Technical architecture
- Methodology or patterns
- Lessons learned

### ✅ Done and Shipped?
1. Update **`CHANGELOG.md`** with the change
2. Mark complete in **`docs/03_planning/02_features.md`**
3. Close any related GitHub issues
4. Optionally log in **`docs/02_history/YYYYMMDD.md`**

### 🗑️ No Longer Relevant?
→ **`docs/09_archive/`**
- Old approaches you replaced
- Deprecated features
- Historical context worth preserving

---

## Idea → Roadmap → Feature: The Three-Stage Pipeline

**This is one of the most important rules in the DNA. Enforce it strictly.**

These three things are NOT interchangeable. Each has a specific home and a specific level of commitment and detail.

---

### Stage 1: Idea (`docs/01_inputs/ideas.md`)
**What it is:** A raw thought. No commitment. No scoping. Just captured.

- "What if we supported voice input?"
- "Could this work as a SaaS?"
- "Maybe add dark mode someday"

**Rules:**
- No effort required to add an idea — low barrier is the point
- Do NOT move things here into planning prematurely
- Ideas can sit here indefinitely — that is fine
- An idea is NOT a commitment

---

### Stage 2: Roadmap (`docs/03_planning/01_roadmap.md`)
**What it is:** Directional intent. Things you've decided are worth pursuing but haven't fully scoped yet.

- Higher-level than features — "build audit tool" not "add `--dry-run` flag"
- Organized by target version (see versioning rules below)
- A roadmap item can represent multiple features
- Still subject to change — direction, not contract

**Rules:**
- Only items you've decided are WORTH doing belong here (not just ideas)
- Each item should answer: What is it? What version does it target?
- Brief descriptions are OK here — full detail goes in features
- Do NOT put crossed-out items in the roadmap — archive or delete them
- Do NOT use phases (Phase 1, Phase 2) — use version numbers

**Format:**
```markdown
## v0.x — [milestone name]
- [ ] Short description of capability or goal
- [ ] Another item

## v1.0 — MVP
- [ ] Everything required to call this project "done enough to ship"
```

---

### Stage 3: Feature (`docs/03_planning/02_features.md`)
**What it is:** A fully scoped, detailed breakdown of a specific capability.

**Rules:**
- Every feature MUST use the required template (see below)
- Features are tied to a specific version number
- Do NOT use crossed-out text in active features — archive or delete completed features
- Do NOT keep stale historical notes in the features file — that belongs in `02_history/`
- Features status must be one of: `Planned` | `In Progress` | `Awaiting Merge` | `Complete`
- Complete features move to `09_archive/completed-features.md` after shipping

**Required Feature Template:**
```markdown
### [Feature Name]
**Status:** Planned | In Progress | Awaiting Merge | Complete
**Target Version:** v0.x
**Priority:** High | Medium | Low

**Description:**
What this feature does in 2-4 sentences. Be specific.

**Why:**
Why does this need to exist? What problem does it solve?

**Acceptance Criteria:**
- [ ] Specific, testable condition that must be true when this is done
- [ ] Another condition
- [ ] And another

**Implementation Notes:** (optional)
Any technical decisions, approach, or constraints worth noting.
```

**What is NOT a valid feature entry:**
- A bullet point with no description
- A crossed-out item
- A note that says "see Phase 2"
- Anything that doesn't have Acceptance Criteria

---

### The Graduation Path

1. **Capture** → `01_inputs/ideas.md` (no filter, no commitment)
2. **Decide it's worth doing** → Promote to `01_roadmap.md` with a target version
3. **Scope it out** → Write a full feature entry in `02_features.md`
4. **Build it** → Update status to "In Progress"
5. **Code complete** → All acceptance criteria checked; update status to "Awaiting Merge"
6. **Ship it** → Merge to `main`; update status to "Complete", move to archive, update `CHANGELOG.md`
7. **Reflect** (optional) → Log anything interesting in `02_history/YYYYMMDD.md`

**Trigger for each transition:**
- Idea → Roadmap: "I've decided this is worth building"
- Roadmap → Feature: "I'm about to start or plan this in detail"
- Feature → Archive: "This is done and shipped"

---

## Versioning System

**All projects use semantic versioning: `MAJOR.MINOR` increments.**

### The Scale
| Version | Meaning |
|---|---|
| `v0.1` | First working prototype — something runs |
| `v0.2` – `v0.9` | Iterative development, features added per increment |
| `v1.0` | **MVP — minimum viable product, shippable to real users** |
| `v1.1`, `v1.2` | Post-MVP improvements and additions |
| `v2.0` | Major rewrite, architectural overhaul, or direction change |

### Rules
- **v0.x is pre-MVP** — the product is not finished, not promised to anyone
- **v1.0 is the milestone you plan toward** — every feature should map to a version ≤ 1.0 or beyond
- **Never use "Phase 1 / Phase 2 / Phase 3"** — use version numbers instead
- **Never use vague labels** like "Near-Term" or "Future" without a version target
- Each `MINOR` increment (0.1 → 0.2) should represent a meaningful, shippable improvement
- `VERSION.txt` always reflects the current deployed/released version
- `CHANGELOG.md` documents what changed at each version

### Example Version Planning
```
v0.1 — Basic scaffolding works, project creates with git init
v0.2 — GitHub repo auto-creation works
v0.3 — Virtual environment setup automated
v0.4 — DNA propagation implemented
v1.0 — MVP: stable, documented, cross-machine, reliable for daily use
v1.1 — Repo audit tool
v1.2 — Cross-platform (Mac/Linux) support
```

---

## ALIGNING EXISTING PROJECTS TO DNA

**If you're integrating an existing project to DNA standards, expect significant restructuring.**

### What the Integration Involves

**Documentation will move around extensively:**
- README bloat → Extract to proper 0-9 folders
- Scattered docs → Consolidate into docs/ structure
- Architecture notes → 05_knowledge/architecture.md
- Roadmap/phases → 03_planning/01_roadmap.md
- Feature status → 03_planning/02_features.md
- Known issues → 03_planning/04_issues.md
- Historical decisions → 02_history/ entries

**Many files will need editing:**
- Add metadata headers to all docs/ markdown files
- Update internal links after moves
- Create new organizational files (roadmap, features, issues)
- Archive old/deprecated docs → 09_archive/

**Source code stays mostly unchanged:**
- Entry points might need reorganization
- But actual application logic is fine

### Use Discernment and Logic

**Where things go requires judgment:**

**Active vs Historical:**
- Still relevant and actionable? → Goes in active folder (03_planning, 05_knowledge)
- No longer relevant but valuable context? → 09_archive/
- Deprecated/obsolete → Delete or document why you're keeping it

**Technical Debt Decision Tree:**
1. **Is it actively causing problems or blocking work?**
   - Yes → `03_planning/04_issues.md` (actionable problem)
   - No, but we need to track it → `05_knowledge/architecture.md` (known limitation)

2. **Is it a historical architecture evolution?**
   - Yes, and it explains current state → `02_history/` entry documenting the transition
   - Yes, but legacy code is still running → Both: issues.md (to fix) + history (context)

3. **Has the old approach been fully replaced?**
   - Yes, old code removed → `09_archive/deprecated.md` (what we replaced and why)
   - No, dual systems coexist → `03_planning/04_issues.md` (needs consolidation)

**Example (Phoenix Chronicle's dual ingestion pipelines):**
- Document in `03_planning/04_issues.md`: "Consolidate IngestorInterface and IngestionPipeline"
- Explain context in `05_knowledge/architecture.md`: "Note: Two interfaces coexist during transition"
- When resolved, document in `02_history/YYYYMMDD.md`: "Completed pipeline consolidation"
- Archive old design in `09_archive/deprecated.md`: "Old IngestorInterface pattern (replaced 2026-02)"

### When Unsure

**Decision hierarchy:**
1. **Check this DNA** - Does it answer your question?
2. **Use self-audit questions** - Apply the 5 questions below
3. **Ask collaborators** - If team project, align on decision
4. **Ask the human** - Project owner makes final call
5. **Document your decision** - Whatever you choose, explain it in the file or commit message

**Better to act with reasoning than freeze from uncertainty.** You can always move things later.

---

## LEARN & BUILD RULES (NEVER VIOLATE)

### Rule 1: Before Writing ANY New Code - Ask "Have We Solved This Before?"
**STOP. Search the codebase FIRST. Check what already works.**

When user requests ANY new feature/script:
1. **Search for similar patterns** - grep/semantic search the codebase
2. **Check past successes** - Read this context file for proven solutions
3. **Check past failures** - Read "Don't Do This" section to avoid repeating mistakes
4. **Ask user:** "I see we have [existing code] that does [similar thing]. Should I start from that?"

### Rule 2: Don't Reinvent the Wheel - Build on What Works
**If something works, COPY it exactly. Modify only what's different.**

- WRONG: "User wants feature X, I'll write it from scratch"
- RIGHT: "User wants feature X. Search codebase... Found Y that's similar. Copy Y, modify for X."

**Common patterns to NEVER recreate:**
- Authentication/login flows
- API integrations (payments, external services)
- Database operations and migrations
- Error handling and retry logic
- Form validation and processing
- Browser automation timing/waits

### Rule 3: Learn from Successes AND Failures
**This context file documents BOTH. Use it.**

**Before coding, check:**
- Past successful patterns documented here
- Known issues and their solutions
- Architecture decisions and why they were made

**If the problem you're solving is mentioned here, USE the documented solution.**

### Rule 4: Cost of Recreating > Cost of Reusing
**Time, money, and trust are expensive. Copy-paste-modify is cheap.**

Recreating solved problems wastes:
- User's time (debugging same issues again)
- User's money (API credits, failed runs, retesting)
- User's trust ("why didn't you check what we already built?")

**Even if copied code "could be cleaner," if it works, keep it working FIRST. Optimize later.**

### Rule 5: When You DO Copy/Reuse - Document It
**Leave breadcrumbs for future-you and future-agents:**

```python
# Copied from working_script.py (proven working since YYYY-MM-DD)
# Modified: [what changed]
# Kept: [what stayed the same - validation, error handling, etc.]
# Why: [reasoning for copying vs creating new]
```

### Rule 6: Code with Empathy
**Write for future you and for anyone who visits this project.**

Every line of code, every comment, every README is read by real people:
- **Future you** - who won't remember why you made that choice
- **Your users** - who are trying to understand how to use your project
- **Contributors** - who want to help but need clear guidance
- **Beginners** - who might be learning from your code

**Code with empathy means:**
- Clear, helpful comments that explain *why*, not just *what*
- Organized structure that makes sense at first glance
- Thoughtful error messages that guide users to solutions
- READMEs that welcome and guide, not gatekeep
- Concise code that prioritizes readability over cleverness

**Ask yourself:**
- "Will someone new to this project understand this?"
- "Would I understand this in 6 months?"
- "Am I making this easy or am I showing off?"

**Remember:** Code is communication. Write it like you're helping someone you care about.

---

## Communication Style Preferences

### When Discussing Code/Design Changes:
- Be literal and precise about file operations
- Use exact verbs: "remove" = delete, "update" = change, "fill in" = replace placeholders, "add" = insert
- Avoid ambiguous language that could trigger alerts
- State what was done, not flowery descriptions

### When Explaining Concepts:
- Be direct and concise
- Ask clarifying questions before assuming
- Explain "why" for design decisions
- Call out when approaching a problem wrong

### When to Stop and Ask:
- If specs are unclear or contradictory
- If technical blocker encountered
- If design decision needed (multiple valid approaches)
- If something could be done multiple ways

### Response Style:
- No emojis (unless user uses them first)
- Concise answers (user values time)
- Get to the point quickly
- Provide examples when explaining

---

## Universal Project Structure Standards

### Entry Point Philosophy

**Core principle:** Projects have ONE clear starting point. Someone cloning your repo should know where to start.

**Implementation varies by project type:**

**Python Scripts:**
- Entry point: `src/main.py`
- Run with: `python src/main.py`
- Simple, direct, one file to find

**Python Packages:**
- Entry point: `src/package_name/main.py`
- Run with: `python -m package_name` or via console script in `pyproject.toml`
- Package structure is standard Python convention

**JavaScript/Node:**
- Entry point: `src/index.js` or `src/app.js`
- Run with: `node src/index.js` or `npm start`

**Other Languages:**
- Rust: `src/main.rs`
- Go: `main.go`
- Follow the language's standard conventions

**What matters:**
- Clear, obvious entry point
- Documented in README how to run it
- All application code in `src/`
- Utility scripts in `scripts/` (build, deploy, maintenance)

### Standard Folder Structure (Expanded with Examples)

```
project-name/
├── src/                    # ALL application code (CODE ONLY - not docs)
│   ├── main.py            # ONLY entry point
│   └── [modules]/         # Organized by function
│
├── scripts/               # Operational/maintenance scripts (NOT application code)
│   └── .gitkeep          # Examples: database re-ingestion, archive cleanup, deployment
│
├── docs/                  # Documentation (0-9 universal framework)
│   │
│   ├── 00_foundation/
│   │   ├── vision.md                    # Why this exists
│   │   ├── values.md                    # Core principles
│   │   └── success-criteria.md          # What "done" looks like
│   │
│   ├── 01_inputs/
│   │   ├── ideas.md                     # Random thoughts, brain dumps
│   │   ├── requests.md                  # Feature requests, customer asks
│   │   └── opportunities.md             # Partnerships, market signals
│   │
│   ├── 02_history/
│   │   ├── 2026-02/                     # Monthly folder (optional)
│   │   │   ├── 20260206.md             # Daily work log
│   │   │   └── 20260207.md
│   │   ├── decisions.md                 # Major decisions log
│   │   └── meetings/                    # Meeting notes (if applicable)
│   │
│   ├── 03_planning/
│   │   ├── 01_roadmap.md                # High-level phases, timeline
│   │   ├── 02_features.md               # Feature list with status
│   │   ├── 03_backlog.md                # Prioritized work queue
│   │   └── 04_issues.md                 # Bugs, problems to fix
│   │
│   ├── 04_creation/
│   │   │
│   │   │   # FOR CODING PROJECTS:
│   │   │   # (Actual code lives in src/ NOT here)
│   │   ├── implementation-notes.md      # Notes ABOUT building
│   │   ├── build-log.md                 # Build process observations
│   │   ├── testing-strategy.md          # How we test
│   │   └── deployment-notes.md          # How we deploy
│   │   │
│   │   │   # FOR WRITING PROJECTS:
│   │   │   # (Actual writing DOES live here - it's markdown)
│   │   ├── chapters/                    # Book chapters
│   │   │   ├── 01-intro.md
│   │   │   └── 02-chapter-two.md
│   │   ├── drafts/                      # Work in progress
│   │   └── fragments/                   # Unplaced scenes, ideas
│   │   │
│   │   │   # FOR BUSINESS/BRAND PROJECTS:
│   │   ├── active-campaigns/            # Marketing campaigns running
│   │   ├── products-in-development/     # What's being built
│   │   └── content-calendar.md          # Publishing schedule
│   │
│   ├── 05_knowledge/
│   │   │
│   │   │   # FOR CODING PROJECTS:
│   │   ├── api-docs.md                  # API reference
│   │   ├── architecture.md              # System design
│   │   ├── setup-guide.md               # Installation instructions
│   │   ├── troubleshooting.md           # Common problems/solutions
│   │   └── dependencies.md              # Why we use each library
│   │   │
│   │   │   # FOR WRITING PROJECTS:
│   │   ├── timeline.md                  # Chronological events
│   │   ├── characters/                  # Character profiles
│   │   ├── world-building.md            # Setting, rules (fiction)
│   │   ├── references.md                # Research sources
│   │   └── style-guide.md               # Voice, tone, formatting
│   │   │
│   │   │   # FOR BUSINESS PROJECTS:
│   │   ├── brand-guidelines/
│   │   ├── sops/                        # Standard operating procedures
│   │   ├── market-research/
│   │   └── learnings/
│   │
│   ├── 06_connections/
│   │   │
│   │   │   # FOR CODING PROJECTS:
│   │   ├── contributors.md              # Who's working on this
│   │   ├── users.md                     # Beta testers, early adopters
│   │   └── integrations.md              # Other systems we connect to
│   │   │
│   │   │   # FOR WRITING PROJECTS:
│   │   ├── beta-readers.md              # Who's reading drafts
│   │   ├── editor.md                    # Editor contact/feedback
│   │   └── people-in-story.md           # Real people mentioned (permissions)
│   │   │
│   │   │   # FOR BUSINESS PROJECTS:
│   │   ├── team/
│   │   ├── customers/
│   │   ├── partners/
│   │   └── community/
│   │
│   ├── 07_resources/
│   │   ├── budget.md                    # Financial resources
│   │   ├── timeline.md                  # Time commitments, deadlines
│   │   ├── tools.md                     # Software/hardware/services used
│   │   └── dependencies.md              # External dependencies
│   │
│   ├── 08_evolution/
│   │   ├── pivots.md                    # Major direction changes
│   │   ├── refactors.md                 # Big code/structure changes
│   │   ├── improvements.md              # How things got better
│   │   └── retrospectives/              # Looking back analyses
│   │
│   └── 09_archive/
│       ├── completed-features.md        # What shipped
│       ├── deprecated.md                # What we removed and why
│       ├── old-versions/                # Historical snapshots
│       └── cut-content/                 # Removed but kept for reference
│
├── data/                  # Project data (gitignored if large)
│   └── .gitkeep
│
├── config/                # Environment-specific config files (.env, YAML, deployment settings)
│   └── .gitkeep          # Application config LOGIC goes in src/<package>/config.py
│
├── logs/                  # Log files (gitignored)
│   └── .gitkeep
│
├── .venv/                 # Virtual environment (gitignored)
│
├── _DNA.md                # Universal AI rules and project context
├── VERSION.txt            # Current version (single line: x.y.z-stage)
├── CHANGELOG.md           # What changed and when
├── README.md              # Project overview
├── requirements.txt       # Python dependencies
├── .gitignore            # Git ignore patterns
└── .env.example          # Environment variables template
```

### Common Framework Exceptions

**You'll see these at root level. They're fine. Document them in your README.**

**Database & Migrations:**
- `alembic/` - SQLAlchemy migrations
- `migrations/` - Django, Rails, or other framework migrations
- `prisma/` - Prisma schema and migrations

**Language/Framework Specific:**
- `node_modules/` - Node.js dependencies (gitignored)
- `.next/` - Next.js build output
- `dist/`, `build/` - Compiled output
- `__pycache__/`, `.pytest_cache/` - Python runtime (gitignored)
- `target/` - Rust build directory

**Application-Managed Storage:**
- `uploads/`, `cache/`, `archive/` - Data the app creates/manages
- Document these in `.gitignore` and README
- If large or sensitive, keep out of git

**When to add root-level folders:**
1. Your framework expects it there (standard convention)
2. Your application creates/manages it (uploads, cache)
3. It's essential to run the project (migrations, config)

**When NOT to add root-level folders:**
- It's documentation/knowledge → `docs/`
- It's source code → `src/`
- It's derived/buildable → `.gitignore` it

---

## Self-Audit Questions

**Use these when your project doesn't match the DNA structure exactly:**

### 1. Is this folder/file standard for my framework or language?
**Examples:** `alembic/`, `node_modules/`, `.next/`, `Cargo.toml`

**Answer:** Keep it where the framework expects it. Document it in your README under "Project Structure" section.

### 2. Does my application create or manage this directory at runtime?
**Examples:** `uploads/`, `cache/`, `archive/`, `exports/`

**Answer:** Keep it at root. Add to `.gitignore` if large or user-specific. Add a comment explaining what it's for.

### 3. Is this knowledge ABOUT the project (not the project itself)?
**Examples:** architecture docs, design decisions, meeting notes, roadmaps, research

**Answer:** It belongs in `docs/` under the 0-9 framework. Even if it's just one file now, it'll grow.

### 4. Does this violate the core principle?
**Core principle:** Docs for thinking, `src/` for doing, root for running

**Ask yourself:**
- Is code scattered outside `src/`? → Violates principle, consolidate it
- Is documentation scattered at root? → Violates principle, move to `docs/`
- Are root-level tools/configs needed to run the project? → Fine, document them

**Answer:** If it violates the principle, restructure. If not, you're good.

### 5. Would someone cloning this repo understand the structure in 30 seconds?
**Test:** Imagine a collaborator (or future you in 6 months) cloning this repo.

**They should immediately see:**
- Where the code lives (`src/`)
- How to run it (README)
- Where docs are (`docs/`)
- What the root files do

**Answer:** If no, add a "Project Structure" section to your README explaining the layout.

### Optional: Test Structure

**Common pattern:** `tests/` mirrors `src/` structure

**Example:**
```
src/
├── main.py
└── phoenix_chronicle/
    ├── core/
    │   ├── storage.py
    │   └── ingestion.py
    └── cli/
        └── commands.py

tests/
├── test_main.py
└── phoenix_chronicle/
    ├── core/
    │   ├── test_storage.py
    │   └── test_ingestion.py
    └── cli/
        └── test_commands.py
```

**This is NOT required** - use whatever test structure makes sense for your framework and team preferences. Common alternatives:
- Flat tests folder (all test files at same level)
- Feature-based organization (tests grouped by feature, not by source file)
- Framework-specific (pytest, Jest, Go test conventions)

**What matters:** Tests exist, they're discoverable, they run reliably.

---

## Documentation Structure (0-9 Universal Framework)

The `docs/` folder uses a **universal 0-9 framework** that works for ANY project type - code, writing, business, personal growth.

### Understanding the DNA: Adaptive Structure

**This folder structure is DNA, not a rigid blueprint.**

DNA guides growth and expression without forcing a specific outcome. Similarly:

- **Simple projects** might only use 3-4 of the 0-9 folders
- **Complex projects** will use all 10 and expand into 10s, 20s, 30s
- **Different project types** use the same folders differently
- **AI creates folders on-demand** as needed, doesn't pre-create everything

**The framework provides:**
- Consistent mental model (where does this go?)
- Adaptive expansion (grow as needed)
- Universal navigation (AI knows the patterns)

**It does NOT provide:**
- Rigid structure (must use all folders)
- Fixed file names (adapt to your needs)
- One-size-fits-all (express based on project type)

### The Universal Thinking Process

Every endeavor requires the same mental steps. The folders reflect this process:

0. **FOUNDATION** - What is this? (Vision, identity, purpose)
1. **INPUTS** - What's coming in? (Ideas, requests, opportunities)
2. **HISTORY** - What happened? (Temporal record, decisions made)
3. **PLANNING** - What's next? (Roadmap, goals, tasks)
4. **CREATION** - What am I building? (Active work, output)
5. **KNOWLEDGE** - What do I know? (Reference, guides, learnings)
6. **CONNECTIONS** - Who's involved? (People, partners, collaborators)
7. **RESOURCES** - What do I have? (Time, money, tools, assets)
8. **EVOLUTION** - How did we grow? (Transformations, pivots, improvements)
9. **ARCHIVE** - What's done? (Completed, closed, historical)

---

### File Metadata Standards

**Every markdown file in `docs/` MUST include metadata header in this exact format:**

```markdown
<sub>**File:** [filename].md</sub>  
<sub>**Created:** YYYY-MM-DD</sub>  
<sub>**Modified:** YYYY-MM-DD</sub>  
<sub>**Purpose:** One-line description of file purpose</sub>
   
---
# [Document Title]
```

**Rules:**
- **Date Format:** YYYY-MM-DD (ISO 8601)
- **Creation Date:** If unknown, use 2026-01-01 as placeholder
- **Modified Date:** Update each time file is edited
- **Purpose:** Clear, concise one-line description
- **Spacing:** Empty line after metadata block, then horizontal rule, then title

**Exemptions (standard root files):**
- `README.md` - Follows its own convention
- `CHANGELOG.md` - Follows Keep a Changelog format
- `LICENSE.md` - Follows license format
- `CONTRIBUTING.md` - Follows contribution guide format

**Why this matters:**
- Quick identification without opening file
- Track when files were created/last updated
- Clear purpose statement for context
- Universal standard across ALL projects
- Maintains clean separation between metadata and content

---

## Individual Folder Descriptions

### 00_foundation/
**Purpose:** Core identity, vision, values - rarely changes

**What goes here:**
- Project vision and purpose
- Core principles and values
- Why this exists
- Success criteria

**When to update:** Major pivots, foundational shifts only

**Typical files:**
- `vision.md` - What we're trying to achieve
- `values.md` - Core principles guiding decisions
- `constraints.md` - Boundaries and limitations
- `success-criteria.md` - What "done" looks like

---

### 01_inputs/
**Purpose:** New things coming in - unprocessed, raw

**THIS IS WHERE ALL IDEAS START.** Don't overthink it. Capture first, organize later.

**What goes here:**
- Random ideas ("What if we added timeline summaries?")
- Feature requests from users
- Opportunities
- Inspirations
- Feedback

**When to update:** Whenever something pops into your head

**Typical files:**
- `ideas.md` - **PRIMARY FILE** - Brain dumps, unfiltered thoughts, all your "what if" moments
- `requests.md` - Things people asked for (external requests)
- `opportunities.md` - Potential collaborations, markets
- `feedback.md` - Customer/user/community feedback

**Critical Rules:**
- **Don't skip this step** - Capture ideas HERE first, not directly in planning
- **No filtering** - Write it down even if you're unsure
- **No commitment required** - Ideas can sit here indefinitely
- **They graduate when you're ready** - When you decide to pursue an idea, move it to `03_planning/`

**Common mistake:** Creating specs in `03_planning/` before capturing in `01_inputs/`. Don't do that. Ideas → Planning, not the reverse.

**Note:** This is the CAPTURE stage. Don't organize here, just dump.

---

### 02_history/
**Purpose:** What happened, when, and why - temporal record

**What goes here:**
- Daily/weekly logs
- Session notes
- Decision log (what was decided and why)
- Meeting notes
- Development journal

**When to update:** Daily or per session

**File naming:** `YYYYMMDD.md` for date-based entries

**Typical files:**
- `2026-02-06.md` - Today's work log
- `2026-02/` - Monthly folder (optional organization)
- `decisions.md` - Major decisions and rationale
- `meetings/` - Meeting notes folder

**Why this matters:** Future you needs to know what happened and why. This is your temporal memory.

---

### 03_planning/
**Purpose:** Future intentions — organized, scoped, version-targeted work

**Required files (always create these):**
- `01_roadmap.md` — Directional intent by version. Brief descriptions, no detail.
- `02_features.md` — Fully scoped features using the required template.

**Optional files (only create if you actually need them):**
- `03_backlog.md` — A prioritized queue of small tasks or sub-tasks too granular for features. **Only create this file if features alone are not enough to track the work.** Most projects never need it.
- `04_issues.md` — Known bugs, broken behavior, regressions. **Only create this if you have actual bugs to track.** Do not create it preemptively.

**Backlog vs Issues vs Features — the difference:**
- **Feature** = new capability being built. Requires full template. Lives in `02_features.md`.
- **Backlog** = small tasks, cleanup, or sub-tasks under an active feature. No template required. Only useful for large features with many moving parts.
- **Issue** = something broken that needs fixing. Not a feature. Not a task. A bug.

**If you're unsure whether something is a feature or an issue:** If it adds new behavior, it's a feature. If it fixes existing broken behavior, it's an issue.

**When to update:** When planning changes, features complete, bugs found/fixed

**How ideas get here:**
- Ideas from `01_inputs/ideas.md` graduate here when you decide to pursue them
- "Graduation" = You're committing time/resources to build it
- Don't create specs here until the idea has been captured in `01_inputs/` first

---

### 04_creation/
**Purpose:** Active work being built RIGHT NOW

**CRITICAL DISTINCTION FOR CODE PROJECTS:**
- **Actual code lives in `src/` - NOT in docs/**
- **This folder contains NOTES ABOUT building, NOT the code itself**
- Think: "documentation of the creation process" not "the creation"

**What goes here:**

**For Code Projects:**
```
04_creation/
├── implementation-notes.md      # Notes while building ("Today discovered X pattern works well")
├── build-log.md                 # Build process observations, gotchas encountered
├── testing-strategy.md          # How we test, what we learned about testing
├── deployment-notes.md          # How we deploy, deployment challenges/solutions
├── code-patterns.md             # Reusable patterns discovered while building
└── performance-notes.md         # Optimization learnings
```
**Remember:** The actual `.py` or `.js` files live in `src/`, NOT here. This folder is for DOCUMENTATION ABOUT the code creation process.

**For Writing Projects:**
```
04_creation/
├── chapters/                    # THE ACTUAL WRITING (markdown files)
│   ├── 01-opening.md
│   ├── 02-rising-action.md
│   └── 03-climax.md
├── drafts/                      # Rough drafts, early versions
│   └── rough-draft-chapter-04.md
├── fragments/                   # Scenes not yet placed in structure
│   ├── flashback-scene.md
│   └── dialogue-snippet.md
└── outlines/                    # Structural outlines
    └── three-act-structure.md
```
**Note:** For writing, the actual content DOES live here because it's markdown documentation.

**For Business/Brand Projects:**
```
04_creation/
├── active-campaigns/            # Marketing campaigns currently running
│   ├── launch-campaign-q1.md
│   └── social-media-push.md
├── products-in-development/     # What's being built right now
│   ├── candid-ai-mvp.md
│   └── phoenix-voice-service.md
├── content-creation/            # Active content production
│   ├── blog-posts-in-progress/
│   └── video-scripts/
└── partnerships-in-progress.md  # Active collaborations
```

**For Mixed Projects (Code + Writing + Business):**
```
04_creation/
├── code-notes/                  # Notes about code being written (NOT the code itself)
│   ├── implementation-log.md
│   └── api-integration-notes.md
├── documentation/               # Docs/guides being written
│   ├── user-guide-draft.md
│   └── api-reference-wip.md
├── campaigns/                   # Marketing/content
│   └── launch-plan.md
└── automation-tools/            # Notes about scripts being built to support project
    └── deployment-automation-notes.md
```

**When to update:** Continuously as you build

**The pattern:** If it's being actively created RIGHT NOW, it lives here. Once complete, it might move to `09_archive/` or stay as ongoing reference.

---

### 05_knowledge/
**Purpose:** What you know - reference material, guides, learnings

**What goes here:**
- SOPs and guides
- Documentation
- How-tos
- Research notes
- Lessons learned
- Data dictionaries

**When to update:** Whenever you learn something worth documenting

**Typical files:**

**For Code Projects:**
- `setup-guide.md` - How to install/run
- `api-docs.md` - API reference
- `architecture.md` - System design
- `troubleshooting.md` - Common problems/solutions
- `dependencies.md` - Why we use each library
- `lessons-learned.md` - What worked/didn't work

**For Writing Projects:**
- `timeline.md` - Chronological events (for memoir/historical)
- `characters/` - Character profiles
- `world-building.md` - Setting, rules (for fiction)
- `references.md` - Research sources
- `style-guide.md` - Voice, tone, formatting rules

**For Business Projects:**
- `brand-guidelines/` - Visual identity, messaging
- `sops/` - Standard operating procedures
- `market-research/` - Competitor analysis, audience insights
- `learnings/` - What works, what doesn't

**Note:** This grows over time. Requires "librarian work" to keep current as knowledge evolves.

---

### 06_connections/
**Purpose:** Who/what is involved - people, partners, relationships

**What goes here:**
- Team members
- Collaborators
- Users/customers
- Partners
- **For writing:** Characters, beta readers

**When to update:** When relationships change

**Typical files:**

**For Code Projects:**
- `contributors.md` - Who's working on this
- `users.md` - Beta testers, early adopters
- `integrations.md` - Other systems we connect to

**For Writing Projects:**
- `beta-readers.md` - Who's reading drafts
- `editor.md` - Editor contact/feedback
- `people-in-story.md` - Real people mentioned (permissions, privacy)

**For Business Projects:**
- `team/` - Employees, contractors, roles
- `customers/` - Customer relationships, key accounts
- `partners/` - Strategic partnerships
- `community/` - Community members, ambassadors

**Note:** May not be used for solo projects, but space exists when needed.

---

### 07_resources/
**Purpose:** What you have - tools, time, money, assets

**What goes here:**
- Budget
- Timeline/schedule
- Tools used
- Dependencies
- Assets

**When to update:** When resources change

**Typical files:**
- `budget.md` - Financial resources, costs
- `timeline.md` - Time commitments, deadlines
- `tools.md` - Software/hardware/services used
- `dependencies.md` - External dependencies, required services
- `assets.md` - IP, brand assets, physical resources

---

### 08_evolution/
**Purpose:** How things changed - transformations, pivots, growth

**What goes here:**
- Major refactors
- Direction changes
- Pivots
- Retrospectives
- Version comparisons

**When to update:** When significant changes happen

**Typical files:**
- `pivots.md` - Major direction changes and why
- `refactors.md` - Big code/structure restructures
- `improvements.md` - How things got better over time
- `retrospectives/` - Looking back analyses (monthly, quarterly)
- `lessons-learned.md` - What we learned from changes

**Note:** Different from `02_history/` - this is about HOW/WHY things evolved, not just what happened day-to-day.

---

### 09_archive/
**Purpose:** Completed, closed, historical - no longer active

**What goes here:**
- Finished features
- Closed issues
- Deprecated approaches
- Old versions
- Cut content

**When to update:** When things complete or become obsolete

**Typical files:**
- `completed-features.md` - What shipped and when
- `deprecated.md` - What we removed and why
- `old-versions/` - Historical snapshots
- `cut-content/` - Removed but kept for reference (e.g., cut chapters)
- `closed-issues.md` - Fixed bugs, resolved problems

---

### Fractal Expansion (When Projects Grow)

**For simple projects:** Just use 00-09

**For complex projects:** Expand themes into 10s, 20s, 30s

**The pattern:**
- **00-09:** Foundation theme (core folders, always present)
- **10-19:** Inputs theme expanded (different types of inputs need separation)
- **20-29:** History theme expanded (different aspects need separate logs)
- **30-39:** Planning theme expanded (strategic vs tactical planning)
- **40-49:** Creation theme expanded (different types of creation work)
- And so on...

**Example - UNIVRSOL business repo:**
```
docs/
├── 00_foundation/
├── 01_inputs/           # General intake
├── 10_customer-requests/  # Expanded: Customer-specific input
├── 11_market-signals/     # Expanded: Market research input
│
├── 02_history/          # General log
├── 20_ops-log/          # Expanded: Operations history
├── 21_decisions/        # Expanded: Strategic decisions
│
├── 03_planning/         # General planning
├── 30_strategy/         # Expanded: Strategic planning
├── 31_product-roadmap/  # Expanded: Product-specific
│
├── 04_creation/         # General creation
├── 40_products/         # Expanded: Product development
├── 41_content/          # Expanded: Content creation
│
├── ...
└── 09_archive/
```

**AI should create expanded folders (10-19, 20-29, etc.) on-demand when needed, not pre-create them.**

---

## Project Type Examples

**The 0-9 framework adapts to different project types. Here are detailed examples:**

### Example 1: Python Coding Project (Candid AI Chatbot)

```
candid-ai/
├── src/                         # Actual Python code
│   ├── main.py
│   ├── chatbot.py
│   └── sms_handler.py
│
├── tests/
│   └── test_chatbot.py
│
├── docs/
│   ├── 00_foundation/
│   │   ├── vision.md            # "Build genuine AI chatbot for small businesses"
│   │   └── principles.md        # "Honest, casual, helpful - not corporate"
│   │
│   ├── 01_inputs/
│   │   ├── ideas.md             # "What if we added voice?" "Multi-language support?"
│   │   └── feature-requests.md  # Customer asks for features
│   │
│   ├── 02_history/
│   │   ├── 2026-02-06.md        # "Today: fixed Twilio integration bug"
│   │   └── decisions.md         # "Why we chose Claude over GPT-4"
│   │
│   ├── 03_planning/
│   │   ├── 01_roadmap.md           # MVP → Beta → v1.0 phases
│   │   ├── 02_features.md          # "SMS support: Complete, Voice: Planned"
│   │   └── 03_issues.md            # "Bug: Response lag on high volume"
│   │
│   ├── 04_creation/
│   │   ├── implementation-notes.md  # "Discovered async helps with lag"
│   │   ├── testing-strategy.md      # "Using pytest + mock Twilio"
│   │   └── deployment-notes.md      # "Deploy via Railway, env vars in dashboard"
│   │   # NOTE: Actual Python code is in src/, NOT here
│   │   # This folder contains NOTES ABOUT building the code
│   │
│   ├── 05_knowledge/
│   │   ├── api-docs.md          # How to use the chatbot API
│   │   ├── architecture.md      # System design diagram
│   │   ├── setup-guide.md       # How to run locally
│   │   └── troubleshooting.md   # Common errors and fixes
│   │
│   ├── 06_connections/
│   │   ├── beta-users.md        # Early customers testing
│   │   └── integrations.md      # Twilio, Claude API, databases
│   │
│   ├── 07_resources/
│   │   ├── costs.md             # API costs, hosting fees
│   │   └── tools.md             # VS Code, Postman, Railway
│   │
│   ├── 08_evolution/
│   │   ├── pivots.md            # "Switched from GPT to Claude for better casual tone"
│   │   └── refactors.md         # "Rewrote message handler for async"
│   │
│   └── 09_archive/
│       └── deprecated-features.md  # "Removed email support - no demand"
```

---

### Example 2: Writing Project (Memoir)

```
memoir/
├── docs/
│   ├── 00_foundation/
│   │   ├── why-this-book.md     # "Integration of inner/outer self"
│   │   ├── themes.md            # "Healing, consciousness, unity"
│   │   └── audience.md          # "People seeking spiritual integration"
│   │
│   ├── 01_inputs/
│   │   ├── story-ideas.md       # "Remember that Ecuador moment..."
│   │   ├── insights.md          # "Realized connection between X and Y"
│   │   └── dreams.md            # Dreams that relate to memoir themes
│   │
│   ├── 02_history/
│   │   ├── 2026-02/
│   │   │   ├── 20260206.md      # "Wrote 1500 words on awakening chapter"
│   │   │   └── 20260207.md      # "Struggled with transition to chapter 5"
│   │   ├── breakthroughs.md     # "Emotional breakthrough writing divorce section"
│   │   └── decisions.md         # "Decided to use non-linear timeline"
│   │
│   ├── 03_planning/
│   │   ├── 01_outline.md           # Full book structure
│   │   ├── 02_chapter-status.md    # Ch 1-3: Complete, Ch 4: In Progress
│   │   └── 03_editing-plan.md      # "First draft by March, edits in April"
│   │
│   ├── 04_creation/             # THE ACTUAL WRITING LIVES HERE
│   │   ├── chapters/
│   │   │   ├── 01-early-years.md
│   │   │   ├── 02-marriage.md
│   │   │   ├── 03-awakening-2021.md
│   │   │   ├── 04-integration-journey.md
│   │   │   └── 05-univrsol-vision.md
│   │   ├── fragments/           # Unplaced scenes
│   │   │   ├── joanna-memories.md
│   │   │   └── kids-moments.md
│   │   └── drafts/              # Early rough versions
│   │
│   ├── 05_knowledge/
│   │   ├── life-timeline.md     # 1982-2026 chronological events
│   │   ├── characters/
│   │   │   ├── jennifer.md      # Ex-wife context
│   │   │   ├── joanna.md        # Significant relationship
│   │   │   └── kids.md          # Isaiah, Joshua, Julia
│   │   ├── references.md        # Books/resources that informed me
│   │   └── style-guide.md       # Voice, tone, Phoenix Voice principles
│   │
│   ├── 06_connections/
│   │   ├── beta-readers.md      # Who's reading drafts
│   │   ├── editor.md            # Editor contact/notes
│   │   └── sensitivity-readers.md  # For cultural/emotional review
│   │
│   ├── 07_resources/
│   │   ├── writing-schedule.md  # Time blocked for writing
│   │   ├── tools.md             # VS Code, AI assistance, Grammarly
│   │   └── budget.md            # Editor costs, cover design
│   │
│   ├── 08_evolution/
│   │   ├── structural-changes.md  # "Moved awakening chapter earlier"
│   │   ├── theme-refinements.md   # How themes evolved
│   │   └── voice-development.md   # How writing voice changed
│   │
│   └── 09_archive/
│       ├── cut-chapters/
│       │   └── removed-chapter-political-rant.md
│       ├── old-outlines/
│       └── first-drafts/
```

---

### Example 3: Mixed Project (UNIVRSOL - Business/Brand/Code/Writing)

```
univrsol/
├── src/                         # Any automation code
│   └── main.py
│
├── projects/                    # Links to other repos
│   ├── memoir/
│   ├── candid-ai/
│   └── phoenix-voice/
│
├── docs/
│   ├── 00_foundation/
│   │   ├── mission.md           # UNIVRSOL core mission
│   │   ├── brand-values.md      # Unity, consciousness, connection
│   │   ├── i-am-everybody.md    # Philosophy foundation
│   │   └── phoenix-voice.md     # Communication framework
│   │
│   ├── 01_inputs/
│   │   ├── ideas-vault.md       # All random business/product ideas
│   │   ├── opportunities.md     # Partnership offers, collabs
│   │   └── feedback.md          # Customer/community feedback
│   │
│   ├── 02_history/
│   │   ├── 2026-02-ecosystem.md  # Monthly ecosystem log
│   │   ├── major-decisions.md    # "Decided to focus on B2B first"
│   │   └── milestones.md         # "Launched Phoenix Voice service"
│   │
│   ├── 03_planning/
│   │   ├── strategic-roadmap.md  # 3-5 year vision
│   │   ├── 2026-goals.md         # This year's objectives
│   │   ├── q1-okrs.md            # Quarterly goals
│   │   ├── project-priorities.md # Which projects to focus on
│   │   └── product-pipeline.md   # What we're building when
│   │
│   ├── 04_creation/
│   │   ├── active-campaigns/
│   │   │   ├── social-media-strategy.md
│   │   │   └── content-calendar.md
│   │   ├── products-in-development/
│   │   │   ├── phoenix-voice-b2b.md
│   │   │   └── listing-pulse-saas.md
│   │   ├── content-creation/
│   │   │   ├── blog-posts/
│   │   │   └── videos/
│   │   └── automation-notes/    # Notes on automation being built
│   │
│   ├── 05_knowledge/
│   │   ├── brand-guidelines/
│   │   │   ├── visual-identity.md
│   │   │   ├── voice-tone.md
│   │   │   └── messaging-framework.md
│   │   ├── sops/
│   │   │   ├── content-creation-process.md
│   │   │   ├── product-launch-checklist.md
│   │   │   └── customer-support-guide.md
│   │   ├── frameworks/
│   │   │   ├── mission-42.md
│   │   │   ├── spectrum-thinking.md
│   │   │   └── angel-numbers.md
│   │   ├── market-research/
│   │   └── learnings/
│   │       ├── what-works.md
│   │       └── what-doesnt.md
│   │
│   ├── 06_connections/
│   │   ├── team/
│   │   ├── community/
│   │   ├── partners/
│   │   └── investors/
│   │
│   ├── 07_resources/
│   │   ├── finances/
│   │   │   ├── budget.md
│   │   │   ├── revenue-streams.md
│   │   │   └── expenses.md
│   │   ├── tools-platforms.md
│   │   ├── assets/
│   │   │   ├── ip-inventory.md
│   │   │   └── brand-assets.md
│   │   └── time-allocation.md
│   │
│   ├── 08_evolution/
│   │   ├── brand-pivots.md          # Major direction changes
│   │   ├── product-iterations.md    # How products evolved
│   │   ├── organizational-changes.md
│   │   ├── market-adaptations.md
│   │   └── retrospectives/
│   │       ├── 2025-retrospective.md
│   │       └── q4-2025-retro.md
│   │
│   └── 09_archive/
│       ├── sunset-projects/
│       │   ├── why-we-stopped-X.md
│       │   └── lessons-from-Y.md
│       ├── old-campaigns/
│       ├── departed-team-members.md
│       └── closed-partnerships.md
```

---

## AI Behavior with This Structure

### When user says "I have an idea for X":
1. AI creates/updates `01_inputs/ideas.md`
2. Captures the idea there
3. Does NOT ask where to put it - AI knows

### When user says "Let's work on feature Y":
1. AI moves idea from `01_inputs/` to `03_planning/features.md`
2. Adds status: In Progress
3. May create spec in `04_creation/` if complex

### When user is actively building:
1. AI tracks work in `04_creation/`
2. Updates `02_history/YYYYMMDD.md` with what happened
3. Documents learnings in `05_knowledge/` as appropriate

### When user says "We changed direction":
1. AI documents in `08_evolution/pivots.md`
2. Updates `02_history/` with the decision
3. May update `00_foundation/` if fundamental shift

### When user completes something:
1. AI moves from `04_creation/` to `09_archive/`
2. Updates `03_planning/` status to Complete
3. Updates CHANGELOG.md

**The AI should know where things go based on the thinking stage, not ask the user.**

---

## Documentation Maintenance (For AI Assistants)

When user says "update my docs" or "I finished [work]", follow this process:

### Ask These Questions First:
1. What did you complete today?
2. Did you fix any bugs? (to close issues)
3. Did you start anything new? (to mark in progress)
4. Is a phase/milestone complete? (version bump needed)
5. Did you update file headers with latest modified date?

### Then Update These Files:

**Always update:**
- `docs/02_history/YYYYMMDD.md` - Add today's entry
- **File headers** - Update Modified date in any docs you edited (format: `YYYY-MM-DD`)

**If feature completed:**
- `docs/03_planning/features.md` - Mark status: Complete
- `CHANGELOG.md` - Add entry under [Unreleased]
- `docs/03_planning/roadmap.md` - Update completion percentage

**If bug fixed:**
- `docs/03_planning/issues.md` - Move to Closed section
- `CHANGELOG.md` - Add entry under [Unreleased]

**If feature started:**
- `docs/03_planning/features.md` - Mark status: In Progress
- Move from `docs/01_inputs/` if it was there
- Create spec in `docs/04_creation/` if needed

**If phase/milestone complete:**
- `VERSION.txt` - Bump version (use target from roadmap.md)
- `docs/03_planning/roadmap.md` - Mark phase complete
- `CHANGELOG.md` - Create release section with version number
- Remind user to: `git tag v[VERSION]`

### Version Numbers Reference:
- Always check `docs/03_planning/roadmap.md` for target versions
- Each phase has a defined target version (e.g., Phase 1 → 0.1.0)
- Use that target version when marking phase complete

### Documentation Synchronization (DRY Principle)

**Rule: Don't Repeat Yourself (DRY) in documentation.**

**Single Source of Truth:**
- Each piece of information should live in ONE authoritative location
- Other docs can REFERENCE it, but shouldn't duplicate it
- Reduces maintenance burden and prevents contradictions

**Where Information Lives:**

| Information Type | Authoritative Location | Can Reference From |
|-----------------|------------------------|--------------------|
| Project purpose/scope | `docs/00_foundation/vision.md` | README.md, other docs |
| Current architecture | `docs/05_knowledge/architecture.md` | Specs, journal entries |
| Feature status | `docs/03_planning/features.md` | Roadmap, journal |
| Version targets | `docs/03_planning/roadmap.md` | CHANGELOG.md |
| Current version | `VERSION.txt` | CHANGELOG.md, docs |

**When Updates Happen, Check Alignment:**

1. **Architecture changes** → Update:
   - `docs/05_knowledge/architecture.md` (authoritative)
   - Check if any specs reference old structure
   - Update journal entry with what changed and why

2. **Feature completion** → Update:
   - `docs/03_planning/features.md` (status: Complete)
   - `CHANGELOG.md` (what was added)
   - `docs/03_planning/roadmap.md` (phase progress if applicable)
   - Journal entry documenting the work

3. **Version bump** → Update:
   - `VERSION.txt` (new version)
   - `CHANGELOG.md` (create release section)
   - `docs/03_planning/roadmap.md` (mark phase complete)
   - Git tag (`git tag v[VERSION]`)

**Acceptable Duplication (Different Perspectives):**
- **README.md** vs **docs/00_foundation/vision.md**
  - README: Brief, user-facing, getting started focus
  - Vision: Detailed, comprehensive, internal reference
  - Keep aligned but different levels of detail

- **CHANGELOG.md** vs **Journal entries**
  - CHANGELOG: What changed (user-facing, release notes)
  - Journal: How/why it changed (developer perspective, decisions)
  - Related but serve different purposes

**Before Completing Updates - Verify:**
1. Did I update the authoritative source?
2. Are there references in other docs that need alignment?
3. Does this change affect VERSION.txt, CHANGELOG.md, or roadmap.md?
4. Would someone reading a different doc be confused by outdated info?

**Ask yourself:** "If I read [other doc] after this update, would it contradict what I just wrote?"

### Quality Assurance & Verification Workflow

**After ANY major code change, integration, or cleanup - ALWAYS run this verification process.**

**Purpose:** Catch inconsistencies, dead links, outdated references, and missing details BEFORE committing. Quality is in the details.

#### Post-Integration Cleanup Checklist

**1. Repository Structure Audit**
- [ ] `@workspace` - Does repo structure match `_DNA.md`?
- [ ] Are there duplicate folders or files?
- [ ] Any orphaned/legacy files that should be deleted or archived?
- [ ] Do folder names follow 0-9 framework conventions?

**2. Documentation Synchronization Audit**
- [ ] `grep_search` for references to deleted files/folders
- [ ] Check all internal links in README.md and docs/
- [ ] Do architecture docs reflect current implementation?
- [ ] Are feature descriptions accurate (not referencing old approaches)?
- [ ] Search for old terminology that's been replaced (e.g., "scaffolds/" → "clone-and-customize")

**3. File Header Maintenance** (CRITICAL - Details Matter)
- [ ] **Every edited file MUST have updated Modified date**
- [ ] Format: `<sub>**Modified:** 2026-02-10</sub>` (YYYY-MM-DD)
- [ ] Check Created date is present (if missing, use placeholder)
- [ ] Purpose line still accurate?
- [ ] **This is NOT optional** - file headers are metadata, not decoration

**4. Code-Documentation Alignment**
- [ ] Does `architecture.md` describe what the code actually does?
- [ ] Are examples in docs using current command syntax?
- [ ] Do error messages/comments match current file structure?
- [ ] Any hardcoded paths that changed?

**5. Git State Verification**
- [ ] `git status` - Review all changes before committing
- [ ] Any unexpected deletions or modifications?
- [ ] Staged vs unstaged - does it match intent?
- [ ] Commit message will be clear about what changed?

#### Questions to Ask Yourself (Before Marking Work Complete)

**Documentation:**
1. "If someone clones this repo tomorrow, will the docs match reality?"
2. "Are there any dead links or references to deleted files?"
3. "Did I update Modified dates on ALL edited files?"
4. "Does README.md still make sense after my changes?"

**Code:**
5. "Does the architecture doc describe what the code actually does?"
6. "Are there any comments referencing old implementations?"
7. "Did I test the happy path AND edge cases?"

**Structure:**
8. "Are there any duplicate files I created/forgot to delete?"
9. "Is everything in the right folder per 0-9 framework?"
10. "Would my past self understand this structure in 6 months?"

**Version Control:**
11. "Does this commit belong on draft or main?"
12. "Is my commit message clear and descriptive?"
13. "Should I squash these changes or keep separate commits?"

#### When to Run Full Audit

**ALWAYS run after:**
- Merging branches (especially after rebases)
- Major refactoring or restructuring
- Deleting old code/folders
- Renaming files or changing architecture
- Integration work spanning multiple days
- Before marking a phase/milestone complete

**Quick audit (questions 1-5 only) after:**
- Adding new features
- Fixing bugs
- Updating documentation
- Any file edits

#### Refinement is NOT "Ask Mode" - It's Quality Control

**This back-and-forth verification process is NORMAL and EXPECTED:**
- Find issues → Fix → Verify → Find more issues → Fix → Verify
- Each iteration makes the repo cleaner and more aligned
- Details matter: file headers, links, terminology consistency
- Quality work requires multiple passes

**AI Assistants:** Don't apologize for iterations. This is the process. Execute each verification step systematically. Update all file headers. Check references. Fix issues. Repeat until clean.

---

## Version Management

### VERSION.txt Format
```
MAJOR.MINOR.PATCH-stage
```

**Examples:**
- `0.1.0-dev` - Phase 1 in development
- `0.1.0` - Phase 1 complete
- `0.2.0` - Phase 2 complete (new features)
- `0.2.1` - Bug fix (no new features)
- `1.0.0` - First production release

**When to bump:**
- `MAJOR` - Breaking changes (1.0.0 → 2.0.0)
- `MINOR` - New features (0.1.0 → 0.2.0)
- `PATCH` - Bug fixes only (0.1.0 → 0.1.1)

**Target versions defined in:** `docs/03_planning/roadmap.md`

---

## Secrets Management

**All secrets are stored as Windows User Environment Variables.**

### Available Environment Variables

The following API keys and secrets are available system-wide (use `os.getenv('VAR_NAME')`):

**API Keys:**
- `ANCHOR_API_KEY`
- `BIRDEYE_API_KEY`
- `GITHUB_TOKEN`
- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`
- `HELIUS_API_KEY`
- `OPENAI_API_KEY`
- `REPLIT_API_KEY`
- `TWOCAPTCHA_API_KEY`

**User Info:**
- `GITHUB_USERNAME`

**Test Data:**
- `TEST_DOB`
- `TEST_EMAIL`
- `TEST_FIRST_NAME`
- `TEST_ID_NUMBER`
- `TEST_LAST_NAME`
- `TEST_PHONE`
- `TEST_SSN_LAST4`

### Accessing Secrets in Code

```python
import os
github_token = os.getenv('GITHUB_TOKEN')
api_key = os.getenv('OPENAI_API_KEY')
database_url = os.getenv('DATABASE_URL')
```

### Rules
- Never hardcode API keys or tokens in code
- Use clear, consistent naming (e.g., `GITHUB_TOKEN`, `OPENAI_API_KEY`)
- All secrets retrieved at runtime via `os.getenv()`
- Never commit secrets to the repo
- No need to create `.env` files - all keys are available system-wide

**For setup instructions, see the project README.**

### .gitignore and Large File Management

#### Add These Before Your First Commit (Every Project)

Always include in .gitignore from day one:

```gitignore
# Large binaries — never commit these
*.pdf
*.PDF
*.docx
*.xlsx
*.csv
*.xml
*.zip
*.tar
*.tar.gz
*.7z
*.rar
*.mp3
*.mp4
*.mov
*.avi
*.png
*.jpg
*.jpeg
*.gif
*.webp
*.tiff
*.tif
*.bmp
*.heic
*.heif

# Project-specific large folders (customize per project)
data/
outputs/
exports/
```

If you add these before the first `git add`, none of these files will ever enter git history. This is the only safe moment.

---

#### If Large Files Were Already Committed — Safe Removal

**ONLY use `git rm --cached`.** This removes files from git tracking without touching them on disk.

```powershell
# Remove a folder from tracking (files stay on disk)
git rm --cached -r path/to/large/folder/

# Then update .gitignore to prevent re-tracking
# Then commit
git commit -m "stop tracking large files, add to .gitignore"
git push
```

Files remain on your machine. Future pushes won't include them. History will contain one last commit with them — that is acceptable.

---

#### `git filter-repo` — When and When NOT to Use

| Situation | Tool |
|---|---|
| Large files already committed, just want to stop tracking | `git rm --cached` |
| Files exist elsewhere, just want gitignore | `git rm --cached` |
| Accidentally committed a password, API key, or secret | `git filter-repo` |
| File must be scrubbed from GitHub's servers entirely | `git filter-repo` |

**`git filter-repo` is a last resort for secrets.** It rewrites all history and **deletes tracked files from your working directory**. Files that existed on disk before the command will be gone afterward if they were tracked by git.

**Before running `git filter-repo`, always:**
1. Copy the files out of the repo folder (to Desktop or a backup location)
2. Confirm with the repo owner what will be deleted
3. Run the command
4. Copy files back
5. Re-add the `origin` remote (`git filter-repo` removes it automatically)
6. Force push: `git push origin <branch> --force`
7. Re-link tracking: `git branch --set-upstream-to=origin/<branch> <branch>`

---

#### Rule

> **Never run `git filter-repo` against tracked files without first confirming the user has a backup copy and understands files will be deleted from disk.**

---

#### Audit Checklist (New Repo Setup)

- [ ] .gitignore includes binary/media types before first commit
- [ ] Large data folders explicitly listed in .gitignore
- [ ] No PDF, image, or binary files appear in `git status` before first push
- [ ] README documents what is gitignored and where those files live locally

---

#### Private Data and Secrets

**Every project may have sensitive files that should never be committed.**

These vary by project but commonly include:
- API response data containing personal information
- Database dumps or exports
- User data files (CSVs, JSON with PII)
- Configuration files with credentials
- Session tokens or cache files
- Project-specific sensitive outputs

**When setting up or auditing a repository:**

1. **Identify private/sensitive files** - what data does this project handle?
2. **Add to `.gitignore`** - prevent future commits
3. **Use `git rm --cached`** if files were already committed but contain no secrets
4. **Use `git filter-repo`** ONLY for secrets that must be purged from history
5. **Document in README** - note what types of files are gitignored and why

**Note:** `.gitignore` only prevents future commits - it does NOT protect already-committed files.

---

## Coding Standards

### Naming Conventions
- **Files:** snake_case.py
- **Functions:** snake_case()
- **Classes:** PascalCase
- **Variables:** snake_case
- **Constants:** UPPER_SNAKE_CASE

### Code Organization
- Keep modules focused (single responsibility)
- Separate configuration from business logic
- Use dependency injection for testability
- Document "why" not "what" in comments

### Testing
- Write tests as you build (not after)
- Test files mirror src/ structure
- Run tests: `pytest tests/ -v`

---

## Git Workflow

### Branch Strategy
**Pablo's preferred workflow: `draft` branch synced with `main`**

- Work on `draft` branch for all development
- When ready to merge: Use **squash and merge** on GitHub
- After squash and merge to main:
  1. `git checkout main`
  2. `git pull` (get the squashed commit)
  3. `git branch -D draft` (delete old diverged branch)
  4. `git checkout -b draft` (fresh draft from main)
  5. `git push -f origin draft` (update remote)

**Why:** Keeps draft and main in sync. The squash creates a new commit, so the old draft branch diverges.

### Commit Message Format
```
[type]: [brief description]

[optional detailed explanation]
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation only
- `refactor:` - Code restructure (no behavior change)
- `test:` - Adding/updating tests
- `chore:` - Maintenance (dependencies, build)

### Tagging Releases
```bash
git tag v0.1.0
git push origin v0.1.0
```

---

## Anti-Patterns (Don't Do This)

### Project Structure:
- Don't create multiple entry points (only main.py)
- Don't put code outside src/ (except scripts/)
- Don't mix configuration with code

### Documentation:
- Don't let docs get stale (update as you work)
- Don't create docs in wrong folders (follow structure)
- Don't duplicate information across files
- Don't create files speculatively — only create files with real content you'll actually use
- Don't create `03_backlog.md` or `04_issues.md` unless you have content to put in them right now

### Version Management:
- Don't skip version bumps when completing phases
- Don't forget to update CHANGELOG.md
- Don't bump major version until 1.0.0 release

### Git:
- Don't commit without a message
- Don't commit directly to main (for team projects)
- Don't forget to tag releases

### Communication:
- Don't use ambiguous language ("clean up", "fix up")
- Don't assume - ask clarifying questions
- Don't over-explain - be concise

---

## Testing and Validation Preferences

### Build Approach:
- Build each component standalone first
- Test as you build (not after everything is done)
- Use dry-run modes when appropriate
- Provide clear success criteria

### When Something Works:
- Document it immediately
- Note why it works
- Save the pattern for reuse

### When Something Fails:
- Document the failure
- Document what was tried
- Document the solution
- Prevent repeating the mistake

---

**Note:** This file is universal across all projects. Project-specific details (tech stack, architecture, current status) live in the `docs/` folder structure.

This file lives in the root of every project and propagates from the scaffolding template.