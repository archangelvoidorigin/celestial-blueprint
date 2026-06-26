---
title: "Stage 3 — The Hands"
tags: [build-plan, stage-3, cli]
status: "Not Started — begin after Stage 1 VERIFY.md passes"
date_created: 2026-06-25
---

# Stage 3 — The Hands

A `cb` CLI that wraps every Celestial Blueprint REST API endpoint. Pure HTTP client — no `app.*` imports, no logic duplication. Agents and shell scripts can create, query, and mutate blueprints without a browser.

**Prerequisite:** Stage 1 complete (backend API running on port 8787). Stage 2 is independent — the CLI does not depend on the agent scanner.

---

## Phase dependency graph

```
P3.1 CLI Core (scaffold → config → client → main entrypoint)
  └─► P3.2 Integration Tests
        └─► P3.3 Fish Completions
              └─► P3.4 Automation + Verification
```

---

## Phases and task count

| Phase | Title | Tasks |
|-------|-------|-------|
| P3.1 | CLI Core | 4 (T3.1.01–04) |
| P3.2 | Integration Tests | 1 (T3.2.01) |
| P3.3 | Fish Completions | 2 (T3.3.01–02) |
| P3.4 | Automation + Verification | 2 (T3.4.01–02) |
| **Total** | | **9 tasks** |

---

## Full task index

| ID | Title | Depends on |
|----|-------|------------|
| T3.1.01 | Scaffold: cli package + pyproject.toml entry point | T1.8.01 |
| T3.1.02 | `cli/config.py` — env + TOML config loader | T3.1.01 |
| T3.1.03 | `cli/client.py` — CelestialClient (all API methods) | T3.1.02 |
| T3.1.04 | `cli/main.py` — argparse tree + `cb` entry point | T3.1.03 |
| T3.2.01 | `tests/test_cli.py` — integration tests via ASGITransport | T3.1.04 |
| T3.3.01 | `cli/completions/cb.fish` — fish completions | T3.1.04 |
| T3.3.02 | `cli/install_completions.sh` + dev.fish reminder | T3.3.01 |
| T3.4.01 | `docs/automation.md` — Hermes + cron automation docs | T3.3.02 |
| T3.4.02 | `BUILD_PLAN/STAGE_3_HANDS/VERIFY.md` — E2E checklist | T3.4.01 |

---

## Stage 3 done when

`cb blueprint list` and `cb blueprint create "My Plan"` work from the terminal; output is valid JSON; `cb blueprint export <id>` dumps parseable markdown; `pytest tests/test_cli.py` passes; fish completions load without error.
