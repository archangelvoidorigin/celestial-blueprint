---
title: "Phase 3.2 — Integration Tests"
tags: [build-plan, stage-3, phase-3.2, tests]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 3.2 — Integration Tests

One test file exercises `CelestialClient` against a real FastAPI app over `httpx.ASGITransport` — no backgrounded uvicorn, no network, full in-process isolation. The fixture pattern mirrors T1.4.08: `monkeypatch.setenv` + `importlib.reload` to isolate each test run's DB.

## Task

| ID | Title | Depends on |
|----|-------|------------|
| T3.2.01 | `tests/test_cli.py` — integration tests | T3.1.04 |

## Done when

`pytest tests/test_cli.py -q` passes (all tests green).
