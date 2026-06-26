---
title: "Phase 1.8 — Verification"
tags: [build-plan, stage-1, phase-1.8, verify]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.8 — Verification

The sign-off phase. Confirm the full stack works end-to-end, the recovery guarantee holds, and the skill loads in real tools.

## Tasks

| Task | Produces | Depends on |
|------|----------|------------|
| T1.8.01 | `VERIFY.md` — E2E manual checklist | all of 1.1–1.7 |
| T1.8.02 | Recovery test (delete DB → `POST /api/rebuild`) | T1.4.06 |
| T1.8.03 | Skill load test in Claude Code + OpenCode | T1.5.07 |

## Stage 1 done when

All boxes in `VERIFY.md` are checked:
- `pytest -q` = all green
- `fish dev.fish` starts both services
- Canvas loads, nodes add, edges connect
- DB delete + rebuild = same data
- Skill loads and interrogates

**Then**: update `00_TASK_INDEX.md` status "In Progress" → "Complete" for Stage 1. Begin Stage 2 decomposition.
