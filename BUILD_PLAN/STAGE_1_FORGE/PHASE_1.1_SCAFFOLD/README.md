---
title: "Phase 1.1 — Scaffold & Tooling"
tags: [build-plan, stage-1, phase-1.1, scaffold]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.1 — Scaffold & Tooling

Lay the foundation: directory tree, backend dependency + config files, frontend Vite/React/TS project with Tailwind + React Flow, and the root run tooling. Nothing else in Stage 1 can start until this phase is done.

## Tasks (run in order)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.1.01 | Full directory tree + `.gitkeep` | none |
| T1.1.02 | `backend/requirements.txt`, `backend/pyproject.toml` | T1.1.01 |
| T1.1.03 | `backend/.env.example`, root `.gitignore` | T1.1.01 |
| T1.1.04 | backend `__init__.py` files + `app/core/config.py` | T1.1.02 |
| T1.1.05 | `frontend/package.json`, `vite.config.ts`, `tsconfig*.json` | T1.1.01 |
| T1.1.06 | `frontend/tailwind.config.js`, `postcss.config.js`, `src/index.css` | T1.1.05 |
| T1.1.07 | `frontend/index.html`, `src/main.tsx`, `src/App.tsx` | T1.1.06 |
| T1.1.08 | root `Makefile`, `dev.fish` | T1.1.04, T1.1.07 |

## Internal dependency graph

```
T1.1.01 ─┬─► T1.1.02 ─► T1.1.04 ─┐
         │                       ├─► T1.1.08
         └─► T1.1.05 ─► T1.1.06 ─► T1.1.07 ─┘
T1.1.01 ─► T1.1.03 (independent)
```

## Phase done when

- `cd backend && make install-backend` builds the venv and imports succeed.
- `cd frontend && npm install && npm run build` succeeds.
- `make -n backend` and `make -n frontend` show the right commands.
- Real secrets (`.env`) and the DB are gitignored.

After this phase, proceed to **Phase 1.2 (Format & Parser)** and **Phase 1.3 (Data Model & DB)** — they can be done in parallel.
