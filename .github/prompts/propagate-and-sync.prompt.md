---
name: propagate-and-sync
description: "Use when: you've updated DNA files and want to push them to all 32 repos, and/or refresh the health dashboard. Runs fully locally — no GitHub Actions consumed."
---

You are propagating DNA changes and/or refreshing the health dashboard. Both operations run locally using the `.venv` Python environment. No GitHub Actions are involved.

Work through each phase in order. Do not skip phases.

---

## Phase 1 — Set Token

Run this first. Everything below depends on it.

```powershell
$env:GITHUB_TOKEN = [System.Environment]::GetEnvironmentVariable('GITHUB_TOKEN','User')
```

Confirm the token is set: `$env:GITHUB_TOKEN.Length` should return a non-zero number. If it returns 0 or empty, stop and ask the user to set `GITHUB_TOKEN` as a Windows user environment variable.

---

## Phase 2 — Propagate DNA (if DNA files changed)

Skip this phase if no DNA files were changed this session. DNA files are: `_DNA.md`, `_UNIVRSOL.md`, `_PHOENIX_VOICE.md`, `CLAUDE.md`, `AGENTS.md`, `requirements.txt`, `.github/copilot-instructions.md`, `.github/workflows/dna-callback.yml`, `.github/prompts/*`.

If DNA files changed, run:

```powershell
.\.venv\Scripts\python scripts/propagate_dna.py --remote
```

This pushes the changed files to all 32 repos. It will take ~2 minutes. Wait for it to complete before continuing.

If it errors with a rate limit or auth error, stop and report the exact error. Do not retry in a loop.

---

## Phase 3 — Refresh Health Dashboard (if requested)

Skip this phase unless the user explicitly asked to refresh the dashboard.

**Important:** The GitHub Models API has a limit of 150 calls/day. Each repo assessment = 1 call. Running all 32 = 32 calls. Check whether you are near the limit before running. If you already ran a full seed today, skip this phase or run only specific repos.

Wipe the existing dashboard and re-seed all repos:

```powershell
Remove-Item docs/05_knowledge/repo-health.md
$repos = @("audio-transcriber","candid-ai","chain-surfer","comicverse","compass","cordova-small-claims","dad-speaks","digital-products","dps-scheduler","finances","folder-cleanup","graceful-messages","kingdom-within","link-detective-json-view","link-sms","listing-pulse","mindflow","nexus","phoenix-chronicle","phoenix-core","pixel-pod-prep","prima-materia","projects","pub_test","replit-backup","spark-dock","spotify-connect","sww-explorer","the-church-of-quantum","tower-clash-analysis","univrsol-logo","univrsol-media-caveman")
foreach ($repo in $repos) { .\.venv\Scripts\python scripts/update_health_dashboard.py $repo }
```

If a repo shows `Assessment=—`, it was either rate-limited or content-filtered. That is acceptable — the `—` fallback is intentional.

---

## Phase 4 — Commit Results

If either phase made changes to local files, commit them:

```powershell
git add -A
git commit -m "chore: Propagate DNA + refresh health dashboard"
git push
```

If on `draft` branch, push to `draft`. Do not merge to `main` here — that is the job of `save-progress-merge`.
