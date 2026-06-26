---
title: "Stage 4 — The Nerves"
tags: [build-plan, stage-4, mcp]
status: "Not Started — begin after Stage 1 VERIFY.md passes"
date_created: 2026-06-24
---

# Stage 4 — The Nerves

An MCP server that exposes Celestial Blueprint as a tool surface so any MCP-capable agent (Claude Code, OpenCode, etc.) can create blueprints, add nodes, log chronicles, and query the registry — without a browser.

**Prerequisite:** Stage 1 complete. Stage 2 and Stage 3 are independent — the MCP server does not depend on them.

---

## Phase dependency graph

```
P4.1 MCP Scaffold (mcp/ dir + requirements)
  └─► P4.2 MCP Server (server.py — full stdio tool surface)
        └─► P4.3 Register (add to mcp-lazy-servers.json)
              └─► P4.4 Skill MCP Wiring (update SKILL.md tool names)
                    └─► P4.5 Verification (VERIFY.md + E2E checklist)
```

---

## Phases and task count

| Phase | Title | Tasks |
|-------|-------|-------|
| P4.1 | MCP Scaffold | 1 (T4.1.01) |
| P4.2 | MCP Server | 1 (T4.2.01) |
| P4.3 | Register | 1 (T4.3.01) |
| P4.4 | Skill MCP Wiring | 1 (T4.4.01) |
| P4.5 | Verification | 1 (T4.5.01) |
| **Total** | | **5 tasks** |

---

## Full task index

| ID | Title | Depends on |
|----|-------|------------|
| T4.1.01 | Scaffold `mcp/` dir + `requirements.txt` | T1.8.01 |
| T4.2.01 | `mcp/server.py` — stdio MCP server (all 14 tools) | T4.1.01 |
| T4.3.01 | Register `celestial-blueprint` in `mcp-lazy-servers.json` | T4.2.01 |
| T4.4.01 | Update `SKILL.md` MCP-mode section with real tool names | T4.3.01 |
| T4.5.01 | `BUILD_PLAN/STAGE_4_NERVES/VERIFY.md` — E2E verification checklist | T4.4.01 |

---

## Stage 4 done when

An agent in Claude Code can call `blueprint_create` and `node_add` via MCP, the DB updates, and the markdown file is rewritten on disk.
