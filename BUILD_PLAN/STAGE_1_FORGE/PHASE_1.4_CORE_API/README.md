---
title: "Phase 1.4 — Core API"
tags: [build-plan, stage-1, phase-1.4, api]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.4 — Core API

The FastAPI service that wraps the store + parser + serializer. **This is the contract** — the React canvas, the future CLI, the MCP server, and agents are all thin clients of these endpoints. Every mutation rewrites the canonical markdown via `files.write_blueprint_file`.

## Tasks (run in order)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.4.01 | `app/main.py` (app, CORS, lifespan) | T1.3.02 |
| T1.4.02 | `app/services/files.py`, `app/api/blueprints.py` | T1.4.01, T1.3.04 |
| T1.4.03 | `app/api/nodes.py` (nodes + edges) | T1.4.01, T1.3.05 |
| T1.4.04 | `app/api/tracking.py` (assumptions/decisions/risks) | T1.4.01, T1.3.05 |
| T1.4.05 | `app/api/chronicles.py` | T1.4.01, T1.3.05 |
| T1.4.06 | `app/api/io.py` (export/import/rebuild) | T1.4.02, T1.2.06 |
| T1.4.07 | `docs/API.md` | T1.4.02–06 |
| T1.4.08 | `tests/test_api.py` | T1.4.07 |

## Router wiring

`main.py` has one `# --- ROUTER INCLUDES ---` block; each router task (T1.4.02–06) appends a two-line `from ... import router; app.include_router(router)` there. Keep them all under that block.

## Hard rules enforced here

- **Every endpoint documented** in `docs/API.md` (T1.4.07).
- **Mutations rewrite markdown** via `write_blueprint_file`.
- **Never delete**: archive endpoint flips status; no DELETE route.
- **Recovery**: `POST /api/rebuild` reconstructs the DB from `blueprints/`.

## Phase done when

`pytest tests/test_api.py` passes and `uvicorn app.main:app --port 8787` serves `/api/health`. This unblocks Phase 1.6 (React Canvas) and the run tooling.
