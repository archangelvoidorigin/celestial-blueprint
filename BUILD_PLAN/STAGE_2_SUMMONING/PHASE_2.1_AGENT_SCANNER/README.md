---
title: "Phase 2.1 — Agent Scanner"
stage: 2
phase: 2.1
status: "not started"
---

# Phase 2.1 — Agent Scanner

Detect every agent runtime installed on the system and produce a JSON manifest at `backend/agents/discovered.json`. Each detector is its own function; `scan_all()` aggregates them and writes the manifest.

**Prerequisite:** Stage 1 complete (backend runs, `GET /api/blueprints` responds 200).

## Task order

| Task | Title | Depends on |
|------|-------|------------|
| T2.1.01 | Scanner module scaffold + helpers | T1.8.01 (Stage 1 done) |
| T2.1.02 | Detect Claude Code | T2.1.01 |
| T2.1.03 | Detect OpenCode | T2.1.01 |
| T2.1.04 | Detect OpenAI Codex CLI | T2.1.01 |
| T2.1.05 | Detect Google Antigravity / Gemini CLI | T2.1.01 |
| T2.1.06 | Detect Hermes | T2.1.01 |
| T2.1.07 | Detect Ollama | T2.1.01 |
| T2.1.08 | Detect custom agents + scan_all() + discovered.json | T2.1.02–07 |

## Phase done when

`python -m agents.scanner` (from `backend/`) exits 0 and writes `agents/discovered.json` with at least one entry.
