---
title: "Celestial Blueprint — Build Plan (How to Use)"
tags: [build-plan, prompt-pack, celestial-blueprint]
status: done
date_created: 2026-06-23
---

# Celestial Blueprint — Build Plan

This folder is a **prompt-pack**: a decomposed build plan where every task is a small, self-contained prompt that a single AI model (even a weaker one) can execute in one sitting without seeing the rest of the project.

## How to use this (for a human orchestrator)

1. Open `00_TASK_INDEX.md` — it lists every task in dependency order.
2. Work top to bottom. For each task:
   - Give the model **two files**: `00_GLOBAL_CONTEXT.md` + the task file (e.g. `STAGE_1_FORGE/PHASE_1.1_SCAFFOLD/T1.1.01_create_directory_structure.md`).
   - Tell it: "Read the global context, then complete this task exactly. Run the Verify Command. Report PASS/FAIL."
   - Mark the task `[x]` in `00_TASK_INDEX.md` only when its Verify Command passes.
3. Do not skip ahead — a task's "Depends on" field lists what must exist first.

## How to use this (for a model executing a task)

You will be handed `00_GLOBAL_CONTEXT.md` and exactly one task file. Do this:
1. Read `00_GLOBAL_CONTEXT.md` fully — it has the paths, stack, and hard rules.
2. Read the task file. Do **only** what it says. Create/edit only the files in its "Produces" list.
3. Run the "Verify Command". If it fails, fix and retry. If you cannot, STOP and report the error — do not invent schema or guess.
4. Report which files you created/changed and the verify result.

## Structure

```
00_README.md            ← you are here
00_GLOBAL_CONTEXT.md    ← read this before every task
00_TASK_INDEX.md        ← master ordered checklist
00_PROMPT_TEMPLATE.md   ← the shape every task file follows

STAGE_1_FORGE/          ← the web app — fully atomized (51 tasks, 8 phases)
STAGE_2..6/             ← fully atomized (all phases + task files written)
```

## Stage order

1. **The Forge** — the web application (backend API + React canvas). Build this fully first.
2. **The Summoning** — discover the AI agents installed on the machine and route planning to them.
3. **The Hands** — a CLI over the API for headless/automation use.
4. **The Nerves** — an MCP server so any agent can drive the planner.
5. **The Brain** — connect to the 9 memory systems + live project state.
6. **The Ascension** — OS-level integration.

Each later stage is decomposed into its own prompt-pack when Stage 1 is done.

## Golden rule

The backend API is the single source of truth for behavior. The React app, CLI, MCP server, and agents are all just clients of it. Never put planning logic anywhere but the backend.
