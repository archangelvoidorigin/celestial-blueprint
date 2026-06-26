---
title: "Phase 1.6 — React Canvas"
tags: [build-plan, stage-1, phase-1.6, frontend]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.6 — React Canvas

The browser client of the API. React 18 + React Flow + Tailwind, dark theme, dot-grid canvas. Every data fetch and mutation goes through `lib/api.ts`. Requires Phase 1.4 (the API) to be running to be useful; the build itself only needs the TypeScript types.

## Tasks (run in order)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.6.01 | `src/lib/api.ts` (typed client, inline type stubs) | T1.1.07, T1.4.07 |
| T1.6.02 | `src/types/blueprint.ts` (formalised types + update api.ts) | T1.1.07, T1.4.07 |
| T1.6.03 | `src/pages/BlueprintList.tsx` | T1.6.01, T1.6.02 |
| T1.6.04 | `src/pages/Canvas.tsx` (React Flow + dark dot-grid) | T1.6.01, T1.6.02 |
| T1.6.05 | `components/nodes/` (4 custom node cards + `nodeTypes`) | T1.6.04 |
| T1.6.06 | `components/canvas/NodeCreator.tsx` | T1.6.05 |
| T1.6.07 | `components/chronicle/ChroniclePanel.tsx` | T1.6.04 |
| T1.6.08 | `App.tsx` + `main.tsx` routing wiring | T1.6.03, T1.6.04 |

## Phase done when

`npm run build` succeeds and `npm run dev` serves:
- `/` → `BlueprintList` (list + create)
- `/blueprint/:id` → `Canvas` (dot-grid graph, node creator, chronicle drawer)

Requires Phase 1.7 (auth) then Phase 1.8 (verification) to confirm the full stack works end-to-end.
