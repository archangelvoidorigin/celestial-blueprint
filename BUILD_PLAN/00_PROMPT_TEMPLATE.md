---
title: "Celestial Blueprint — Task Prompt Template"
tags: [build-plan, template]
status: done
date_created: 2026-06-23
---

# Task Prompt Template

Every `T*.md` task file in this build plan follows this exact structure. Copy this when writing a new task (e.g. when atomizing Stages 2–6).

```markdown
# TASK T<stage>.<phase>.<nn> — <Imperative Title>

- **Stage / Phase**: Stage <n> — <Name> / Phase <n>.<m>
- **Depends on**: <comma-separated T-ids, or "none">
- **Produces**: <exact file path(s) created or modified>

## Context
<2–4 sentences. What this is part of, what already exists from prior tasks,
why it matters. Fully self-contained: assume the model has seen ONLY
00_GLOBAL_CONTEXT.md and this file.>

## Objective
<One sentence: the single concrete outcome.>

## Instructions
<Numbered steps. For code tasks, give the FULL file content in a fenced code
block (preferred) OR exact edits with enough surrounding context to be
unambiguous. Always use absolute or root-relative paths. Zero ambiguity.>

## Acceptance Criteria
- [ ] <verifiable condition>
- [ ] <verifiable condition>

## Verify Command
```bash
<copy-paste command that proves the task is done>
```
Expected: <exact expected output or observable result>

## Done When
<One sentence describing the finished state.>
```

## Rules for writing tasks

1. **One unit of work** per task — a single file, function, component, or config. If it needs "and", consider splitting.
2. **Self-contained** — never say "as in the previous task". Restate the needed context.
3. **Exact content** — prefer giving the full file body over describing it. Weaker models fill gaps badly.
4. **Always verifiable** — every task ends with a command whose output proves success.
5. **Honest dependencies** — "Depends on" must list every prior task whose output this one reads.
6. **No forward references** — a task may only depend on lower-numbered tasks.
