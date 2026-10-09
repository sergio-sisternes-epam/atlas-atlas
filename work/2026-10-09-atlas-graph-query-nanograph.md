---
type: work
title: "Graph queries for Atlas, and whether nanograph replaces BM25"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: implementing
description: "Approved 2026-10-09 (revision 1), implementing: keep SQLite FTS5 as BM25, make --engine bm25 real, add a dependency-free atlas graph surface for discuss, add a nanograph export, gate any nanograph driver."
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

**Approved** by Sergio on 2026-10-09 at 13:54 BST with a direction change (driver overlay; nanograph on macOS arm64 only). Implementing. Plan: [2026-10-09-atlas-graph-query-nanograph](../autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md).

## Outcome in one line

Complement, not replace. FTS5 stays; `--engine bm25` becomes real; `atlas graph nodes|edges|neighbours|export` lands natively; nanograph gets an export and an optional driver behind a driver overlay, enabled only on macOS arm64 with a detected binary.
