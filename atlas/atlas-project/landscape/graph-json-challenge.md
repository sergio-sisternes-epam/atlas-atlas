---
type: document
title: "Challenge — we do not need graph.json"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: alive
kva: alive
description: "think-challenge of the claim that Atlas core graph replaces graph.json. SoR claim holds; projection and schema-evolution counters remain."
origin: derived
sensitivity: internal
relates_to:
  - path: atlas-project/vision.md
    kind: related
  - path: atlas-project/landscape/graphify.md
    kind: counters
  - path: atlas-project/landscape/graphify-inspiration.md
    kind: related
  - path: atlas-project/landscape/md-graph.md
    kind: related
  - path: atlas-project/landscape/sqlite-vec.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Claim challenged

Pages plus `relates_to` plus SCHEMA are the graph. `graph.json` is a patch for things you will not lift into Atlas. Extensible schema is how others compile.

## Counters kept

Materialized views still earn their keep when the source *is* the graph, if the same hops are queried often. Schema extension is not free: required-field and remove-field changes break old readers. Foreign corpora (AST, PDF) stay outside Atlas on purpose.

## What survived

Do not commit Graphify-style `graph.json` as SoR. Optional compile projection (memory, sqlite, Cartograph) is a cache, same family as mesh.json and Azure maps.
