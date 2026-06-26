---
title: "Phase 5.4 — Project-State Connector"
tags: [build-plan, stage-5, phase-5.4]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 5.4 — Project-State Connector

Allow blueprints to reference a CHAOS_DAO_FORGE realm. When the blueprint is loaded, the API reads the realm's `smart-folder.md` and injects a `realm_context` object into the response.

## Task order

```
T5.4.01  app/services/realm.py (read smart-folder.md by realm slug or path)
  └─► T5.4.02  Inject realm_context into GET /api/blueprints/{id}
```

## Done when

`GET /api/blueprints/{id}` response includes `"realm_context": {...}` when the blueprint's `realm` frontmatter field resolves to a readable `smart-folder.md`.
