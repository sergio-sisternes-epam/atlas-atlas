---
type: experience
title: "Implement query-path harness and spine hubs (0.7.7)"
created: 2026-08-27
work_id: 2026-08-27-atlas-query-harness-hubs
status: closed
origin: internal
sensitivity: internal
implements: 2026-08-27-atlas-query-harness-hubs
closes: 2026-08-27-atlas-query-harness-hubs
plan_path: autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md
construct_eval: deferred
description: "Approved hardening: query rewrite from glossary, two spines, SKILL 0.7.7. No search.py change. Construct deferred — no scenario in this slice."
relates_to:
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: implements
  - path: autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md
    kind: related
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
---

## Context

Operator approved plan `2026-08-27-atlas-query-harness-hubs` and asked for an old-vs-new search benchmark after implement.

## What happened

Applied only the approved hardening scope. Baseline searches were recorded before spine pages existed.

## construct_eval

`deferred: design parked adversarial suite until FTS5 or hit-card CLI; this slice is path prose + documents.`

## Changed files

- `references/paths/query.md`
- `references/paths/remember.md`
- `SKILL.md`
- `apm.yml`
- `references/atlas/glossary.md`
- `references/atlas/atlas-project/cli-surface-evolution.md`
- `references/atlas/atlas-project/index.md`
- `references/atlas/work/atlas-bm25-and-live-migration-v1.md`
- `references/atlas/work/2026-08-27-atlas-query-harness-hubs.md`
- `references/atlas/autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md`
- `references/atlas/experiences/2026-08-27-implement-query-harness-hubs.md`
- `references/atlas/experiences/index.md`
- `references/atlas/work/index.md`
- `references/atlas/log.md`
- `artifacts/atlas-query-harness-baseline-2026-08-27.txt` (benchmark input, outside store)

## Outcome

Atlas 0.7.7. Compile required after persist.

## Benchmark (same store, grep engine)

Raw queries unchanged in top-3. Gains appear only after the glossary rewrite or when scoring the new spine pages.

| Query | Target | Before | After |
|-------|--------|--------|-------|
| `bm25` | work hub | rank 4, score 11 | rank 4, score 13 |
| `bm25` + aliases | work hub | n/a | **rank 1, score 45** |
| NL “cli evolve” | spine (did not exist) | — | rank 8, score 22 |
| `cli surface` | spine | — | rank 5, score 17 |
| `CLI surface evolution` | spine | — | rank 3, score 24 |
| `cli surface` + verb aliases | spine | — | rank 11 (plans soak the extra tokens) |

Raw files: `artifacts/atlas-query-harness-baseline-2026-08-27.txt`, `artifacts/atlas-query-harness-after-2026-08-27.txt`.
