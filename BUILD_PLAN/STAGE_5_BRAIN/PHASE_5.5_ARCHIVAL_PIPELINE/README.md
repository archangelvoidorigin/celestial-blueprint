---
title: "Phase 5.5 — Archival Pipeline"
tags: [build-plan, stage-5, phase-5.5]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 5.5 — Archival Pipeline

When a blueprint is archived, move its markdown file from `blueprints/` to a configurable OMNI archive directory. The DB row is never deleted; only the file moves.

## Task order

```
T5.5.01  app/services/archiver.py + CELESTIAL_ARCHIVE_DIR config
  └─► T5.5.02  Wire archiver into POST /api/blueprints/{id}/archive
        └─► T5.5.03  VERIFY.md (stage 5 E2E checklist)
```

## Done when

`POST /api/blueprints/{id}/archive` moves the blueprint's markdown file to `CELESTIAL_ARCHIVE_DIR/{bid}.md`, the DB record stays with status=archived, and VERIFY.md exists.
