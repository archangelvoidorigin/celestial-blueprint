---
title: "Phase 2.3 — Capability Profiles"
stage: 2
phase: 2.3
status: "not started"
---

# Phase 2.3 — Capability Profiles

Define the capability vocabulary and a static map from agent id to capability set. The
scanner uses this map as the source of truth; individual detectors may override specific
capabilities.

**Prerequisite:** Phase 2.2 complete (agents API live).

## Capability vocabulary

| Capability | Meaning |
|------------|---------|
| `research` | Web search, document retrieval |
| `code_gen` | Write / edit code |
| `critique` | Review, flag issues, suggest improvements |
| `summarise` | Summarise documents or sessions |
| `plan` | Produce structured plans, blueprints |
| `file_ops` | Read / write / move files |
| `web_search` | Direct internet search |
| `mcp_tools` | Can call MCP-registered tools |

## Task order

| Task | Title | Depends on |
|------|-------|------------|
| T2.3.01 | `backend/agents/capability_map.py` | T2.2.05 |
| T2.3.02 | Wire capability map into scanner + rescan endpoint | T2.3.01 |

## Phase done when

`scan_all()` returns agents with capabilities drawn from `capability_map.py`; the map can be
overridden via a `--capabilities` flag (CLI, T3.x) later.
