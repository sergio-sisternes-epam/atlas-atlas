---
type: work
title: "Mesh-level indexing: one mesh graph and federated recall across mounted Atlases"
created: 2026-10-10
work_id: 2026-10-10-atlas-mesh-level-index
status: designed
description: "Designed 2026-10-10, awaiting approval: structure-only mesh graph at .atlas/indexes/<type>/_mesh/ with atlas:// node ids and a strict cross-store resolver, plus recall run --scope mesh fusing each member's own index with tiered RRF (k=60). Six follow-up packets after atlas PR #61 merges."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-10-10-atlas-mesh-level-index.md
    kind: related
  - path: autogenesis/experiences/2026-10-10-design-atlas-mesh-level-index.md
    kind: records
  - path: work/2026-10-09-atlas-graph-query-nanograph.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: related
---

## Scope

Sergio asked on 2026-10-10 for mesh-level indexing: one graph across every Atlas a project mounts, and a mesh-wide recall that fuses each store's own index with Reciprocal Rank Fusion, while respecting store privacy and keeping single-store behaviour unchanged.

## Status

**Designed, awaiting Sergio's explicit approval.** Plan: [2026-10-10-atlas-mesh-level-index](../autogenesis/plans/2026-10-10-atlas-mesh-level-index.md). Base: atlas PR #61 (`feat/graph-query-drivers`, head `57198e4`, not merged). Packets land as follow-up PRs after PR #61 merges.

## Outcome in one line

Structure-only mesh graph plus federated tiered-RRF recall, opt-in by `--scope mesh`, promoted only if the multi-Atlas benchmark meets its pre-registered criteria.
