---
title: "Phase 1.5 — Methodology Skill"
tags: [build-plan, stage-1, phase-1.5, skill]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.5 — Methodology Skill

The behaviour spec that makes Celestial Blueprint a *planning* tool. Usable standalone (any agent that loads SKILL.md) without the backend. Built incrementally — each task appends one section. Independent of the backend phases; can run in parallel after T1.2.01 (FORMAT.md).

## Tasks (run in order — each appends to SKILL.md)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.5.01 | `SKILL.md` created: frontmatter + tier-selection | T1.2.01 |
| T1.5.02 | Append: BLANK SLATE interrogation (6 steps) | T1.5.01 |
| T1.5.03 | Append: chronicle protocol (7 triggers, RAW/CYCLE formats) | T1.5.02 |
| T1.5.04 | Append: per-tier output templates | T1.5.03 |
| T1.5.05 | Append: degradation modes + agent roster + definition of done | T1.5.04 |
| T1.5.06 | `reference/interrogation.md`, `reference/chronicle-{raw,cycle}.md` | T1.5.05 |
| T1.5.07 | `link_skill.sh` (symlink to ~/.claude/skills etc.) | T1.5.06 |

## Structure of SKILL.md when complete

```
frontmatter (name, description)
Step 0 — Select the tier
Step 1 — BLANK SLATE interrogation
Step 2 — Chronicle as you go
Step 3 — Produce the blueprint
Operating modes (degradation)
Agent roster
Definition of done
```

## Phase done when

`bash link_skill.sh` completes without errors and the skill loads in Claude Code (`/skills list` shows `celestial-blueprint`). Can run in parallel with Phases 1.2 and 1.3. Does not block 1.4 or 1.6.
