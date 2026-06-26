---
title: "Phase 5.3 — Chronicle Long-Term Query"
tags: [build-plan, stage-5, phase-5.3]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 5.3 — Chronicle Long-Term Query

Search across ALL blueprints' chronicles in a single query, surfacing relevant past session notes during planning.

## Task order

```
T5.3.01  GET /api/chronicles/search?q= (cross-blueprint chronicle search)
```

## Done when

`GET /api/chronicles/search?q=drift` returns matching chronicle entries from any blueprint.
