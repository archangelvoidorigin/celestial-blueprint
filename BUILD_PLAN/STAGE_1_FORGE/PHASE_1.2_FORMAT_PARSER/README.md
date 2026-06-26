---
title: "Phase 1.2 — Format & Parser"
tags: [build-plan, stage-1, phase-1.2, parser]
status: "Not Started"
date_created: 2026-06-24
---

# Phase 1.2 — Format & Parser

Turn blueprint markdown into a canonical JSON dict and back, losslessly. This is the heart of "markdown is canonical": every API mutation rewrites markdown via the serializer; every import re-reads it via the parser. `docs/FORMAT.md` (T1.2.01, already done) is the contract this phase implements.

## Tasks (run in order)

| Task | Produces | Depends on |
|------|----------|------------|
| T1.2.01 | `docs/FORMAT.md` | — (DONE) |
| T1.2.02 | `docs/templates/{small,medium,large,continuous}.md` | T1.2.01 |
| T1.2.03 | `parser.py`: frontmatter + anchor helpers + dict shape | T1.1.04, T1.2.02 |
| T1.2.04 | `parser.py`: summary, categories, nodes | T1.2.03 |
| T1.2.05 | `parser.py`: tracking sections, edges, versions, `parse_blueprint` | T1.2.04 |
| T1.2.06 | `serializer.py`: dict → markdown | T1.2.05 |
| T1.2.07 | `tests/test_roundtrip.py` | T1.2.06 |

## The canonical blueprint dict

Defined in T1.2.03; every parser/serializer task and the store/API layers use this shape:
`frontmatter, summary, categories[], nodes[], assumptions[], decisions[], risks[], research[], chronicle_links[], edges[], versions[]`.

## Phase done when

`pytest tests/test_roundtrip.py` passes — `parse(serialize(parse(md))) == parse(md)` for all four tiers. The parser/serializer pair is the only code allowed to read/write blueprint markdown.

Independent of Phase 1.3 (Data Model). Both feed Phase 1.4 (Core API).
