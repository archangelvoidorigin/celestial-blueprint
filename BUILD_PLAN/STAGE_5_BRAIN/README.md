---
title: "Stage 5 — The Brain"
tags: [build-plan, stage-5, brain, memory]
status: "Not Started — begin after Stage 4 VERIFY.md passes"
date_created: 2026-06-25
---

# Stage 5 — The Brain

Connect Celestial Blueprint to the persistent CHAOS_DAO_FORGE memory and project systems. Blueprints gain context from past sessions, observe real-world drift vs plan, search chronicles across sessions, read project realm state, and archive themselves to the OMNI extraction vault.

**Prerequisite:** Stage 1 complete (T1.8.01). P5.1.03 additionally requires Stage 4 complete (T4.5.01). Phases 5.1–5.5 are otherwise independent of each other and can be built in parallel.

---

## Phase dependency graph

```
T1.8.01 (Stage 1 complete)
├─► P5.1 Memory Bridge → T5.1.01 → T5.1.02 → T5.1.03 (also needs T4.5.01)
├─► P5.2 Observer      → T5.2.01 → T5.2.02
│                               └─► T5.2.03
├─► P5.3 Chronicle Search → T5.3.01
├─► P5.4 Realm Connector  → T5.4.01 → T5.4.02
└─► P5.5 Archival Pipeline → T5.5.01 → T5.5.02
                                              └─► T5.5.03 VERIFY (deps all phases)
```

---

## Phases and task count

| Phase | Title | Tasks |
|-------|-------|-------|
| P5.1 | Memory Bridge | 3 (T5.1.01–03) |
| P5.2 | Observer | 3 (T5.2.01–03) |
| P5.3 | Chronicle Search | 1 (T5.3.01) |
| P5.4 | Realm Connector | 2 (T5.4.01–02) |
| P5.5 | Archival Pipeline | 3 (T5.5.01–03) |
| **Total** | | **12 tasks** |

---

## Full task index

| ID | Title | Depends on |
|----|-------|------------|
| T5.1.01 | `app/services/memory.py` — brain query service | T1.8.01 |
| T5.1.02 | `GET /api/blueprints/{id}/memory-context` endpoint | T5.1.01 |
| T5.1.03 | MCP `memory_query` tool added to `mcp/server.py` | T5.1.02, T4.5.01 |
| T5.2.01 | `tools/observer.py` — blueprint vs reality diff | T1.8.01 |
| T5.2.02 | `POST /api/blueprints/{id}/observe` endpoint | T5.2.01 |
| T5.2.03 | Hermes observer schedule + `docs/automation.md` update | T5.2.01 |
| T5.3.01 | `GET /api/chronicles/search?q=` cross-blueprint search | T1.8.01 |
| T5.4.01 | `app/services/realm.py` — read realm smart-folder.md | T1.8.01 |
| T5.4.02 | Inject `realm_context` into `GET /api/blueprints/{id}` | T5.4.01 |
| T5.5.01 | `app/services/archiver.py` + `CELESTIAL_ARCHIVE_DIR` config | T1.8.01 |
| T5.5.02 | Wire archiver into `POST /api/blueprints/{id}/archive` | T5.5.01 |
| T5.5.03 | `BUILD_PLAN/STAGE_5_BRAIN/VERIFY.md` E2E checklist | T5.1.03, T5.2.03, T5.3.01, T5.4.02, T5.5.02 |

---

## Stage 5 done when

Memory query returns snippets from the brain; observer creates drift assumptions; chronicle search returns cross-blueprint results; realm_context appears in blueprint GET; archiving a blueprint moves its file to the OMNI archive.
