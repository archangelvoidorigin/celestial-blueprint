---
title: "Phase 3.1 — CLI Core"
tags: [build-plan, stage-3, phase-3.1, cli]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 3.1 — CLI Core

Bootstrap the `cb` CLI: Python package structure, config loading, the HTTP client class, and the argparse command tree registered as the `cb` entry point in `pyproject.toml`.

**All code lives in `backend/cli/`. The CLI is installed into the same venv as the backend via `pip install -e .`, but it never imports `app.*`.**

## Task order

```
T3.1.01  Scaffold (package + pyproject.toml)
  └─► T3.1.02  config.py (env + TOML loader)
        └─► T3.1.03  client.py (CelestialClient)
              └─► T3.1.04  main.py (argparse + cb entry point)
```

## Done when

`cb --help` prints the command tree after `pip install -e .`.
