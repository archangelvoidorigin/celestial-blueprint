---
title: "Phase 5.1 — Memory Bridge"
tags: [build-plan, stage-5, phase-5.1]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 5.1 — Memory Bridge

Query the CHAOS_DAO_FORGE brain-orchestrator for context relevant to a blueprint's topic and surface it as `research` node seeds.

## Task order

```
T5.1.01  memory.py service (subprocess brain-orchestrator call)
  └─► T5.1.02  GET /api/blueprints/{id}/memory-context endpoint
        └─► T5.1.03  MCP memory_query tool (+ Stage 4 complete)
```

## Done when

`GET /api/blueprints/{id}/memory-context` returns a list of memory snippets; `memory_query` MCP tool calls the endpoint and returns results; all degrade gracefully to empty list if brain-orchestrator is not configured.
