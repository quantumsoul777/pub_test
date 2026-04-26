# Agent Instructions

**Read `_DNA.md` in the root of this repository before taking any action.**
It is the full source of truth for project structure, planning rules, and AI behavior.

---

## Critical Rules (TL;DR)

### Before Writing Any Code
- A feature entry must exist in `docs/03_planning/02_features.md` using the full required template
- The user must explicitly approve it after reading the spec
- A conversation is not approval. Enthusiasm is not approval. Ask if unsure.

### File Creation
- Only create files with real content you will use right now
- Do not create files speculatively ("might be useful", "for structure", "just in case")
- Features belong in `docs/03_planning/02_features.md` as entries — not as separate files per feature

### Planning Structure
- Raw ideas → `docs/01_inputs/ideas.md`
- Decided direction, not yet scoped → `docs/03_planning/01_roadmap.md`
- Fully scoped work → `docs/03_planning/02_features.md` (full template required)
- Use version numbers (`v0.1`, `v0.2`, `v1.0`) — never "Phase 1", "Phase 2", or "Near-Term"

### If Instructions Are Unclear or Missing
Ask the user. Do not invent structure. Do not make assumptions. The DNA exists so you don't have to guess — if something isn't covered here, ask before acting.

---

Full rules, structure standards, versioning, git workflow, and coding standards: **`_DNA.md`**

For any content creation: **`_PHOENIX_VOICE.md`** — the UNIVRSOL writing standard. Also read **`_UNIVRSOL.md`** for mission context. All repos are UNIVRSOL.
