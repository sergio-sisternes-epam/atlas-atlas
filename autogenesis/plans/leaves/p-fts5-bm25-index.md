---
type: protostar
title: "FTS5 BM25 index in .atlas/index.sqlite"
created: 2026-08-27
work_id: atlas-bm25-and-live-migration-v1
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "Next index packet after query-harness hubs. Title-weighted FTS5, rebuild on compile, not mergeable across branches."
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md
    kind: derived_from
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: implements
  - path: atlas-project/landscape/sqlite-vec.md
    kind: related
---

## Pending

Implement real BM25 only after the query-harness plan is done or explicitly waived.

## Origin

Self-Atlas BM25 idea query + sqlite-vec landscape protostar.
