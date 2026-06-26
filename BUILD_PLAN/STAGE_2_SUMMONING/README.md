---
title: "Stage 2 — The Summoning"
tags: [build-plan, stage-2, agent-discovery]
status: "Not Started — begin after Stage 1 VERIFY.md passes"
date_created: 2026-06-24
---

# Stage 2 — The Summoning

Scan the system for all installed agent runtimes (Claude Code, OpenCode, Codex, Antigravity,
Hermes, Ollama) and build an agent registry so Celestial Blueprint knows what it can delegate
to.

**Prerequisite:** Stage 1 complete and verified (`BUILD_PLAN/STAGE_1_FORGE/VERIFY.md` passes).

---

## Phase dependency graph

```
P2.1 Agent Scanner
  └─► P2.2 Agent Registry (DB + API)
        └─► P2.3 Capability Profiles
              └─► P2.4 Routing Layer
                    └─► P2.5 Registry UI
```

---

## Phases and task count

| Phase | Title | Tasks |
|-------|-------|-------|
| P2.1 | Agent Scanner | 8 (T2.1.01–08) |
| P2.2 | Agent Registry (DB + API) | 5 (T2.2.01–05) |
| P2.3 | Capability Profiles | 2 (T2.3.01–02) |
| P2.4 | Routing Layer | 3 (T2.4.01–03) |
| P2.5 | Registry UI | 3 (T2.5.01–03) |
| **Total** | | **21 tasks** |

---

## Full task index

| ID | Title | Depends on |
|----|-------|------------|
| T2.1.01 | Scanner module scaffold + helpers | T1.8.01 |
| T2.1.02 | Detect Claude Code | T2.1.01 |
| T2.1.03 | Detect OpenCode | T2.1.01 |
| T2.1.04 | Detect OpenAI Codex CLI | T2.1.01 |
| T2.1.05 | Detect Google Antigravity / Gemini CLI | T2.1.01 |
| T2.1.06 | Detect Hermes | T2.1.01 |
| T2.1.07 | Detect Ollama | T2.1.01 |
| T2.1.08 | Detect custom agents + scan_all() + discovered.json | T2.1.02–07 |
| T2.2.01 | Agents table schema + init_agents() | T2.1.08 |
| T2.2.02 | Pydantic models for Agent | T2.2.01 |
| T2.2.03 | Agent store functions | T2.2.02 |
| T2.2.04 | Agents API router | T2.2.03 |
| T2.2.05 | Wire agents router + update API.md | T2.2.04 |
| T2.3.01 | capability_map.py | T2.2.05 |
| T2.3.02 | Wire capability map into scanner | T2.3.01 |
| T2.4.01 | Routing service | T2.3.02 |
| T2.4.02 | Route API endpoint | T2.4.01 |
| T2.4.03 | Wire route router + update API.md | T2.4.02 |
| T2.5.01 | Agents page (Agents.tsx) | T2.4.03 |
| T2.5.02 | Wire Agents route + nav in App.tsx | T2.5.01 |
| T2.5.03 | Stage 2 verification checklist | T2.5.02 |

---

## Stage 2 done when

`GET /api/agents` returns at least one discovered agent; `POST /api/route` returns a valid
routing decision; the frontend `/agents` tab shows the registry; all checks in
`STAGE_2_SUMMONING/VERIFY.md` pass.
