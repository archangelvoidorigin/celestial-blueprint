---
title: "Phase 2.4 — Routing Layer"
stage: 2
phase: 2.4
status: "not started"
---

# Phase 2.4 — Routing Layer

`POST /api/route` accepts a `{task_type, context}` payload and returns the best available
agent + its activation command. Priority: prefer local `active` agents with the matching
capability; fallback to `claude-code` (or whichever model is cheapest) for everything.

**Prerequisite:** Phase 2.3 complete (capability map wired).

## Task order

| Task | Title | Depends on |
|------|-------|------------|
| T2.4.01 | `backend/app/services/router.py` | T2.3.02 |
| T2.4.02 | `backend/app/api/router.py` endpoint | T2.4.01 |
| T2.4.03 | Wire router + document in API.md | T2.4.02 |

## Phase done when

`POST /api/route {"task_type": "code_gen"}` returns a JSON object with `agent_id` and
`activation_cmd`.
