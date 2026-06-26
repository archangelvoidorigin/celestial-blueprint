---
title: "Phase 3.3 — Fish Completions"
tags: [build-plan, stage-3, phase-3.3, fish, completions]
status: "Not Started"
date_created: 2026-06-25
---

# Phase 3.3 — Fish Completions

Generate fish shell tab-completions for all `cb` subcommands and flags, and provide an install script that symlinks the completions file into `~/.config/fish/completions/`.

## Tasks

| ID | Title | Depends on |
|----|-------|------------|
| T3.3.01 | `cli/completions/cb.fish` — fish completions | T3.1.04 |
| T3.3.02 | `cli/install_completions.sh` + dev.fish reminder | T3.3.01 |

## Done when

`fish -c "source backend/cli/completions/cb.fish; complete -C 'cb '" | head -5` lists at least 5 completions; `install_completions.sh` creates the symlink.
