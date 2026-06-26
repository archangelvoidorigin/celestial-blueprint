---
title: "Phase 1.3 — Data Model & DB"
tags: [build-plan, stage-1, phase-1.3, database]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.3 — Data Model & DB

The SQLite query index and the store layer that reads/writes it. Markdown stays canonical; this DB is rebuildable from markdown via import. The store is the only module that touches SQL — the API calls the store, never raw queries.

## Tasks (run in order)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.3.01 | `app/models/schema.sql` (8 tables, WAL/FK) | T1.1.04 |
| T1.3.02 | `app/core/db.py` connection + init | T1.3.01 |
| T1.3.03 | `app/models/schemas.py` Pydantic models | T1.1.04 |
| T1.3.04 | `app/services/store.py` blueprint CRUD | T1.3.02, T1.3.03 |
| T1.3.05 | `store.py` child entities + save/get/archive | T1.3.04 |
| T1.3.06 | `tests/test_store.py` | T1.3.05 |

## 8 tables

`blueprints` (+ JSON cols for categories/research/chronicle_links), `nodes`, `edges`, `assumptions`, `decisions`, `risks`, `chronicles`, `versions`. All child tables cascade-delete with their blueprint and are scoped by `blueprint_id`.

## Key invariants

- **Never delete**: `archive_blueprint` flips status to `archived`; no destructive delete in the store.
- **Round-trip**: `save_blueprint(parse_blueprint(md))` → `get_blueprint(id)` reconstructs the canonical dict.
- **Frontmatter is authoritative**: denormalized columns (name/tier/status/version) are kept in sync with `frontmatter_json` on every write.

## Phase done when

`pytest tests/test_store.py` passes. Can run in parallel with Phase 1.2; both are prerequisites for Phase 1.4 (Core API).
