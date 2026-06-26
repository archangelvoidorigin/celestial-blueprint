---
title: "Phase 2.2 — Agent Registry (DB + API)"
stage: 2
phase: 2.2
status: "not started"
---

# Phase 2.2 — Agent Registry (DB + API)

Persist discovered agents in SQLite. Expose CRUD + rescan endpoints under `/api/agents`.

**Prerequisite:** Phase 2.1 complete (`scan_all()` works, `discovered.json` written).

## Task order

| Task | Title | Depends on |
|------|-------|------------|
| T2.2.01 | Agents table schema + init_agents() | T2.1.08 |
| T2.2.02 | Pydantic models for Agent | T2.2.01 |
| T2.2.03 | Store functions for agents | T2.2.02 |
| T2.2.04 | API router `app/api/agents.py` | T2.2.03 |
| T2.2.05 | Wire router + update API.md | T2.2.04 |

## Phase done when

`GET /api/agents` returns a JSON list; `POST /api/agents/scan` triggers discovery and
populates the DB; at least one agent appears.
