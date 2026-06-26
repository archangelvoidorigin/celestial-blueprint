---
title: "Phase 5.2 — Observer"
tags: [build-plan, stage-5, phase-5.2]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 5.2 — Observer

A standalone script and API endpoint that compares a blueprint's declared plan against real project state (git log, file modification times) and auto-logs drift as assumption or chronicle entries.

## Task order

```
T5.2.01  tools/observer.py (standalone script)
  ├─► T5.2.02  POST /api/blueprints/{id}/observe endpoint
  └─► T5.2.03  Hermes schedule + docs/automation.md update
```

## Done when

`python3 tools/observer.py` runs against the API, detects stale blueprints, and logs assumption entries; `POST /api/blueprints/{id}/observe` does the same on demand; Hermes task file exists.
