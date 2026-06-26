---
title: "Celestial Blueprint — Master Task Index"
tags: [build-plan, index, checklist]
status: "In Progress"
date_created: 2026-06-23
---

# Master Task Index

Execute in this order. Check a box only when the task's Verify Command passes. No task depends on a higher-numbered task.

## STAGE 1 — THE FORGE (web application)

### Phase 1.1 — Scaffold & Tooling
- [ ] T1.1.01 — Create full directory structure · deps: none
- [ ] T1.1.02 — Backend dependency files · deps: T1.1.01
- [ ] T1.1.03 — Backend `.env.example` + `.gitignore` · deps: T1.1.01
- [ ] T1.1.04 — Backend package init + `app/core/config.py` · deps: T1.1.02
- [ ] T1.1.05 — Frontend Vite + React + TS init · deps: T1.1.01
- [ ] T1.1.06 — Frontend Tailwind + React Flow config · deps: T1.1.05
- [ ] T1.1.07 — Frontend base shell · deps: T1.1.06
- [ ] T1.1.08 — Root Makefile + `dev.fish` · deps: T1.1.04, T1.1.07

### Phase 1.2 — Format & Parser
- [x] T1.2.01 — `docs/FORMAT.md` (DONE before build plan)
- [ ] T1.2.02 — Tier templates (small/medium/large/continuous) · deps: T1.2.01
- [ ] T1.2.03 — Parser: frontmatter · deps: T1.1.04, T1.2.02
- [ ] T1.2.04 — Parser: categories + nodes · deps: T1.2.03
- [ ] T1.2.05 — Parser: decisions/assumptions/risks/research/edges/versions · deps: T1.2.04
- [ ] T1.2.06 — Serializer: JSON → markdown · deps: T1.2.05
- [ ] T1.2.07 — Round-trip tests · deps: T1.2.06

### Phase 1.3 — Data Model & DB
- [ ] T1.3.01 — `app/models/schema.sql` (8 tables) · deps: T1.1.04
- [ ] T1.3.02 — `app/core/db.py` connection/init · deps: T1.3.01
- [ ] T1.3.03 — `app/models/schemas.py` Pydantic models · deps: T1.1.04
- [ ] T1.3.04 — `app/services/store.py` blueprint CRUD · deps: T1.3.02, T1.3.03
- [ ] T1.3.05 — `store.py` child-entity CRUD · deps: T1.3.04
- [ ] T1.3.06 — `tests/test_store.py` · deps: T1.3.05

### Phase 1.4 — Core API
- [ ] T1.4.01 — `app/main.py` FastAPI app + CORS + lifespan · deps: T1.3.02
- [ ] T1.4.02 — `app/api/blueprints.py` · deps: T1.4.01, T1.3.04
- [ ] T1.4.03 — `app/api/nodes.py` (nodes + edges) · deps: T1.4.01, T1.3.05
- [ ] T1.4.04 — `app/api/tracking.py` (assumptions/decisions/risks) · deps: T1.4.01, T1.3.05
- [ ] T1.4.05 — `app/api/chronicles.py` · deps: T1.4.01, T1.3.05
- [ ] T1.4.06 — `app/api/io.py` import/export · deps: T1.4.02, T1.2.06
- [ ] T1.4.07 — `docs/API.md` · deps: T1.4.02, T1.4.03, T1.4.04, T1.4.05, T1.4.06
- [ ] T1.4.08 — `tests/test_api.py` · deps: T1.4.07

### Phase 1.5 — Methodology Skill
- [ ] T1.5.01 — SKILL.md frontmatter + tier-selection · deps: T1.2.01
- [ ] T1.5.02 — SKILL.md interrogation protocol · deps: T1.5.01
- [ ] T1.5.03 — SKILL.md chronicle protocol · deps: T1.5.02
- [ ] T1.5.04 — SKILL.md tier output templates · deps: T1.5.03
- [ ] T1.5.05 — SKILL.md degradation + agent roster · deps: T1.5.04
- [ ] T1.5.06 — `reference/` interrogation + chronicle templates · deps: T1.5.05
- [ ] T1.5.07 — `link_skill.sh` symlink installer · deps: T1.5.06

### Phase 1.6 — React Canvas
- [ ] T1.6.01 — `lib/api.ts` typed API client · deps: T1.1.07, T1.4.07
- [ ] T1.6.02 — `types/blueprint.ts` · deps: T1.1.07, T1.4.07
- [ ] T1.6.03 — `pages/BlueprintList.tsx` · deps: T1.6.01, T1.6.02
- [ ] T1.6.04 — `pages/Canvas.tsx` React Flow + theme · deps: T1.6.01, T1.6.02
- [ ] T1.6.05 — `components/nodes/` node components · deps: T1.6.04
- [ ] T1.6.06 — `components/canvas/NodeCreator.tsx` · deps: T1.6.05
- [ ] T1.6.07 — `components/chronicle/ChroniclePanel.tsx` · deps: T1.6.04
- [ ] T1.6.08 — Routing + App.tsx layout · deps: T1.6.03, T1.6.04

### Phase 1.7 — Auth & Run
- [ ] T1.7.01 — `app/core/auth.py` local token · deps: T1.1.04
- [ ] T1.7.02 — Auth middleware + frontend token header · deps: T1.7.01, T1.6.01
- [ ] T1.7.03 — `dev.fish` run script · deps: T1.1.08
- [ ] T1.7.04 — `docker-compose.yml` (optional/deferred) · deps: T1.4.08

### Phase 1.8 — Verification
- [ ] T1.8.01 — E2E manual checklist (`VERIFY.md`) · deps: all of 1.1–1.7
- [ ] T1.8.02 — Recovery test (delete DB, reimport) · deps: T1.4.06
- [ ] T1.8.03 — Cross-tool skill-load test · deps: T1.5.07

## STAGE 2 — THE SUMMONING (agent discovery)

### Phase 2.1 — Agent Scanner
- [ ] T2.1.01 — Scanner module scaffold + helpers · deps: T1.8.01
- [ ] T2.1.02 — Detect Claude Code · deps: T2.1.01
- [ ] T2.1.03 — Detect OpenCode · deps: T2.1.01
- [ ] T2.1.04 — Detect OpenAI Codex CLI · deps: T2.1.01
- [ ] T2.1.05 — Detect Google Antigravity / Gemini CLI · deps: T2.1.01
- [ ] T2.1.06 — Detect Hermes · deps: T2.1.01
- [ ] T2.1.07 — Detect Ollama · deps: T2.1.01
- [ ] T2.1.08 — Detect custom agents + scan_all() + discovered.json · deps: T2.1.02–07

### Phase 2.2 — Agent Registry (DB + API)
- [ ] T2.2.01 — Agents table schema + init_agents() · deps: T2.1.08
- [ ] T2.2.02 — Pydantic models for Agent · deps: T2.2.01
- [ ] T2.2.03 — Agent store functions · deps: T2.2.02
- [ ] T2.2.04 — Agents API router · deps: T2.2.03
- [ ] T2.2.05 — Wire agents router + update API.md · deps: T2.2.04

### Phase 2.3 — Capability Profiles
- [ ] T2.3.01 — `capability_map.py` · deps: T2.2.05
- [ ] T2.3.02 — Wire capability map into scanner · deps: T2.3.01

### Phase 2.4 — Routing Layer
- [ ] T2.4.01 — Routing service (`app/services/router.py`) · deps: T2.3.02
- [ ] T2.4.02 — Route API endpoint (`app/api/router.py`) · deps: T2.4.01
- [ ] T2.4.03 — Wire route router + update API.md · deps: T2.4.02

### Phase 2.5 — Registry UI
- [ ] T2.5.01 — `Agents.tsx` page + Agent type + api.ts methods · deps: T2.4.03
- [ ] T2.5.02 — Wire Agents route + nav in `App.tsx` · deps: T2.5.01
- [ ] T2.5.03 — Stage 2 verification checklist (`VERIFY.md`) · deps: T2.5.02

## STAGE 3 — THE HANDS (cb CLI)

### Phase 3.1 — CLI Core
- [ ] T3.1.01 — Scaffold: cli package + pyproject.toml entry point · deps: T1.8.01
- [ ] T3.1.02 — `cli/config.py` env + TOML config loader · deps: T3.1.01
- [ ] T3.1.03 — `cli/client.py` CelestialClient (all API methods) · deps: T3.1.02
- [ ] T3.1.04 — `cli/main.py` argparse tree + `cb` entry point · deps: T3.1.03

### Phase 3.2 — Integration Tests
- [ ] T3.2.01 — `tests/test_cli.py` via ASGITransport · deps: T3.1.04

### Phase 3.3 — Fish Completions
- [ ] T3.3.01 — `cli/completions/cb.fish` fish completions · deps: T3.1.04
- [ ] T3.3.02 — `cli/install_completions.sh` + dev.fish reminder · deps: T3.3.01

### Phase 3.4 — Automation + Verification
- [ ] T3.4.01 — `docs/automation.md` Hermes + cron docs · deps: T3.3.02
- [ ] T3.4.02 — `BUILD_PLAN/STAGE_3_HANDS/VERIFY.md` E2E checklist · deps: T3.4.01

## STAGE 4 — THE NERVES (MCP server)

### Phase 4.1 — MCP Scaffold
- [ ] T4.1.01 — Scaffold `mcp/` dir + `requirements.txt` · deps: T1.8.01

### Phase 4.2 — MCP Server
- [ ] T4.2.01 — `mcp/server.py` stdio MCP server (14 tools) · deps: T4.1.01

### Phase 4.3 — Register
- [ ] T4.3.01 — Register `celestial-blueprint` in `mcp-lazy-servers.json` · deps: T4.2.01

### Phase 4.4 — Skill MCP Wiring
- [ ] T4.4.01 — Update `SKILL.md` MCP-mode section with real tool names · deps: T4.3.01

### Phase 4.5 — Verification
- [ ] T4.5.01 — `BUILD_PLAN/STAGE_4_NERVES/VERIFY.md` E2E checklist · deps: T4.4.01

## STAGE 5 — THE BRAIN

### Phase 5.1 — Memory Bridge
- [ ] T5.1.01 — `app/services/memory.py` brain query service · deps: T1.8.01
- [ ] T5.1.02 — `GET /api/blueprints/{id}/memory-context` endpoint · deps: T5.1.01
- [ ] T5.1.03 — MCP `memory_query` tool · deps: T5.1.02, T4.5.01

### Phase 5.2 — Observer
- [ ] T5.2.01 — `tools/observer.py` blueprint vs reality diff · deps: T1.8.01
- [ ] T5.2.02 — `POST /api/blueprints/{id}/observe` endpoint · deps: T5.2.01
- [ ] T5.2.03 — Hermes observer schedule + automation.md update · deps: T5.2.01

### Phase 5.3 — Chronicle Search
- [ ] T5.3.01 — `GET /api/chronicles/search?q=` cross-blueprint search · deps: T1.8.01

### Phase 5.4 — Realm Connector
- [ ] T5.4.01 — `app/services/realm.py` realm context service · deps: T1.8.01
- [ ] T5.4.02 — Inject `realm_context` into `GET /api/blueprints/{id}` · deps: T5.4.01

### Phase 5.5 — Archival Pipeline
- [ ] T5.5.01 — `app/services/archiver.py` + `CELESTIAL_ARCHIVE_DIR` config · deps: T1.8.01
- [ ] T5.5.02 — Wire archiver into `POST /api/blueprints/{id}/archive` · deps: T5.5.01
- [ ] T5.5.03 — `BUILD_PLAN/STAGE_5_BRAIN/VERIFY.md` E2E checklist · deps: T5.1.03, T5.2.03, T5.3.01, T5.4.02, T5.5.02

## STAGE 6 — THE ASCENSION (OS integration)

### Phase 6.1 — Global Hotkey / Launcher
- [ ] T6.1.01 — `hypr/celestial.conf` keybind fragment + `hypr/link_hypr.sh` · deps: T1.8.01, T3.1.04
- [ ] T6.1.02 — `docs/keybinds.md` · deps: T6.1.01

### Phase 6.2 — Hyprland Integration
- [ ] T6.2.01 — Windowrules + toggle keybind (append to `hypr/celestial.conf`) · deps: T6.1.01
- [ ] T6.2.02 — `tools/toggle_celestial.sh` · deps: T1.8.01

### Phase 6.3 — Notifications
- [ ] T6.3.01 — `tools/notify.sh` CYCLE chronicle → dunst notification · deps: T1.8.01
- [ ] T6.3.02 — `ChroniclePanel.tsx` Web Notification after CYCLE POST · deps: T1.6.07, T6.3.01

### Phase 6.4 — Phone-as-VPS [OPTIONAL]
- [ ] T6.4.01 — `Dockerfile` (multi-arch) + `docker-compose.arm.yml` + `.dockerignore` · deps: T1.8.01
- [ ] T6.4.02 — `docs/phone-vps.md` · deps: T6.4.01

### Phase 6.5 — Always-On Service
- [ ] T6.5.01 — `systemd/celestial-backend.service` + `link_service.sh` · deps: T1.8.01
- [ ] T6.5.02 — `tools/celestial_startup.fish` + `docs/automation.md` Stage 6 · deps: T6.5.01
- [ ] T6.5.03 — `BUILD_PLAN/STAGE_6_ASCENSION/VERIFY.md` E2E checklist · deps: T6.1.02, T6.2.02, T6.3.01, T6.5.02

---

**Stage 1 total: 51 tasks** (T1.2.01 pre-done). **Stage 2 total: 21 tasks.** **Stage 3 total: 9 tasks.** **Stage 4 total: 5 tasks.** **Stage 5 total: 12 tasks.** **Stage 6 total: 11 tasks** (T6.4.01–02 optional). **Grand total: 109 tasks.**
