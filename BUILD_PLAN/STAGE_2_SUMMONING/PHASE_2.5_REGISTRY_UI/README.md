---
title: "Phase 2.5 — Registry UI"
stage: 2
phase: 2.5
status: "not started"
---

# Phase 2.5 — Registry UI

Add an "Agents" tab to the React frontend. Shows the discovered agent registry with status
badges, capability chips, and a Rescan button that hits `POST /api/agents/scan`.

**Prerequisite:** Phase 2.4 complete (routing endpoint live).

## Task order

| Task | Title | Depends on |
|------|-------|------------|
| T2.5.01 | `frontend/src/pages/Agents.tsx` | T2.4.03 |
| T2.5.02 | Wire Agents route + nav into App.tsx | T2.5.01 |
| T2.5.03 | Stage 2 verification checklist | T2.5.02 |

## Phase done when

Browser at `http://localhost:5173/agents` renders a list of discovered agents with status
and capability badges; Rescan button updates the list.
