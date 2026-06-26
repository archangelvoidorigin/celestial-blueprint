---
title: "Stage 1 — The Forge"
tags: [build-plan, stage-1, web-app]
status: "In Progress"
date_created: 2026-06-23
---

# Stage 1 — The Forge

Build the Celestial Blueprint web application: an API-first FastAPI backend plus a React Flow canvas. When this stage is done you can run a tiered, interrogation-driven planning session and see it on a canvas, with blueprints persisted as portable markdown + SQLite.

## Phase dependency graph

```
1.1 Scaffold ──┬─► 1.2 Format & Parser ──┐
               │                          ├─► 1.4 Core API ──► 1.6 React Canvas ──┐
               └─► 1.3 Data Model & DB ───┘         │                              ├─► 1.8 Verify
                                                     ▼                              │
                                          1.5 Methodology Skill ───────────────────┤
                                                     1.7 Auth & Run ───────────────┘
```

- **1.1 Scaffold** — directories, deps, base shells. Nothing else runs without it.
- **1.2 Format & Parser** — turn blueprint markdown ⇄ JSON. Depends on FORMAT.md.
- **1.3 Data Model & DB** — SQLite schema + Pydantic + store layer.
- **1.4 Core API** — FastAPI endpoints wrapping the store + parser. The contract.
- **1.5 Methodology Skill** — the SKILL.md (usable standalone, independent of backend).
- **1.6 React Canvas** — first client of the API.
- **1.7 Auth & Run** — local token auth + dev runner.
- **1.8 Verification** — prove it all works end to end.

## Phases can partly parallelize

- 1.5 (skill) is independent of the backend — can be done any time after 1.2.01 (FORMAT.md).
- 1.2 and 1.3 can be done in parallel after 1.1.
- 1.6 needs 1.4 (the API) to be useful.

## Build order

Follow `../00_TASK_INDEX.md` top to bottom for the safe linear order.
