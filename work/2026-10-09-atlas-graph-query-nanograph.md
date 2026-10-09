---
type: work
title: "Graph queries for Atlas, and whether nanograph replaces BM25"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: designed
description: "Designed, awaiting approval: keep SQLite FTS5 as BM25, make --engine bm25 real, add a dependency-free atlas graph surface for discuss, add a nanograph export, gate any nanograph driver."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
    kind: related
  - path: autogenesis/experiences/2026-10-09-design-atlas-graph-query-nanograph.md
    kind: records
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: follows
---

## Scope

Sergio asked (2026-10-09) for a formal design to discuss, and possibly replace, Atlas's BM25 approach with nanograph, with the discuss skill as a key consumer.

## Status

**Designed**, awaiting explicit approval. Plan: [2026-10-09-atlas-graph-query-nanograph](../autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md).

## Outcome in one line

Complement, not replace. FTS5 stays; `--engine bm25` becomes real; `atlas graph nodes|edges|neighbours|export` lands natively; nanograph gets an export now and a driver only behind gate G-N.
