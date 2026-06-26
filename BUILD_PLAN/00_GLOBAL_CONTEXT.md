---
title: "Celestial Blueprint — Global Build Context"
tags: [build-plan, context, celestial-blueprint]
status: done
date_created: 2026-06-23
---

# GLOBAL CONTEXT — read this before every task

You are building **Celestial Blueprint**, a tiered planning system. Read this file fully, then execute the single task file you were given. Do not do work outside that task.

## 1. Absolute paths

- **Project root**: `/home/void-yggdrasil/CHAOS_DAO_FORGE/00_CORTEX/01_CREATION_REALM/Celestial_Blueprint/`
- All relative paths in task files are relative to this project root unless they start with `/` or `~`.
- **Backend**: `<root>/backend/` (Python FastAPI service)
- **Frontend**: `<root>/frontend/` (Vite + React + TypeScript)
- **Skill**: `<root>/skill/celestial-blueprint/`
- **Docs**: `<root>/docs/` (FORMAT.md, API.md, templates)
- **Blueprints (data)**: `<root>/blueprints/`
- **Chronicles (data)**: `<root>/chronicles/`
- **SQLite DB**: `/home/void-yggdrasil/.claude/projects/-home-void-yggdrasil-CHAOS-DAO-FORGE/memory/celestial.db`

## 2. Stack (exact)

Backend:
- Python 3.11+
- FastAPI 0.115.x, Uvicorn 0.32.x (standard)
- Pydantic 2.x
- PyYAML 6.x (frontmatter parsing)
- sqlite3 (Python standard library — NOT an external package)
- pytest 8.x, httpx 0.27.x (tests)

Frontend:
- Node 20+, Vite 5.x
- React 18.x, TypeScript 5.x
- React Flow (`reactflow` 11.x) — canvas
- Tailwind CSS 3.x
- react-router-dom 6.x

Shell: the user runs **fish**, not bash. venv activation is `source .venv/bin/activate.fish`. Where a task gives a bash command, the intent still holds; adapt activation to fish.

## 3. Run commands

```bash
# Backend (from <root>/backend)
python -m venv .venv
source .venv/bin/activate.fish      # fish shell
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8787

# Frontend (from <root>/frontend)
npm install
npm run dev                          # serves on http://localhost:5173
```

Backend serves on **port 8787**. Frontend dev server proxies `/api` to it (configured in vite.config.ts).

## 4. The data model (source of truth)

`<root>/docs/FORMAT.md` is the authoritative spec for the blueprint file format, the 13 node types, and the round-trip contract. When a task involves blueprint structure, node types, or markdown parsing, **read FORMAT.md first**. Do not invent fields not in FORMAT.md.

Top-level blueprint entities: `blueprints, nodes, edges, assumptions, decisions, risks, chronicles, versions`.

The 13 node types: `text, metric, chart, list, quote, research, assumption, decision, chronicle, agent, cost, realm, tool`.

## 5. Naming conventions

- Blueprint ID: `bp_{YYYY-MM-DD}_{kebab-slug}` (e.g. `bp_2026-06-23_temporal-snowflake`).
- Python: snake_case modules and functions, PascalCase classes.
- TypeScript: camelCase variables, PascalCase components and types.
- Files in `docs/` and `BUILD_PLAN/`: UPPER_SNAKE for docs, descriptive lower for data.

## 6. The 5 hard rules (never break)

1. **API-first.** ALL planning logic lives in the backend. The frontend only calls the API and renders results. Never put validation, parsing, or business logic in React.
2. **Markdown is canonical.** The blueprint `.md` file is the source of truth. The SQLite DB is a rebuildable index. Every backend write that changes a blueprint must also rewrite its markdown file.
3. **Never commit secrets.** `.env` is git-ignored. Only `.env.example` (no real values) is committed.
4. **Never delete blueprints.** Archiving flips `status` and moves the file; deletion is forbidden.
5. **Document endpoints.** Every API endpoint must appear in `docs/API.md`.

## 7. Failure protocol

If a task's Verify Command fails and you cannot fix it within the task's scope:
- STOP.
- Report the exact error and which step failed.
- Do NOT improvise the schema, invent fields, install extra packages, or modify files outside the task's "Produces" list.

## 8. Already present (do not recreate)

These exist before any task runs:
- `README.md`, `smart-folder.md` (project root)
- `docs/FORMAT.md` (the format spec — task T1.2.01, already done)
- Empty `backend/`, `frontend/`, `skill/`, `docs/`, `blueprints/`, `chronicles/` directory trees (task T1.1.01 confirms/completes them)
