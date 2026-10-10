---
type: work
title: "Mesh-level indexing: one mesh graph and federated recall across mounted Atlases"
created: 2026-10-10
work_id: 2026-10-10-atlas-mesh-level-index
status: approved
description: "Approved 2026-10-10 23:08 BST (MA, MB, MC, MF now; MD, ME after MB and MC review; build after atlas PR #61 merges): structure-only mesh graph at .atlas/indexes/<type>/_mesh/ with atlas:// node ids and a strict cross-store resolver, plus recall run --scope mesh fusing each member's own index with tiered RRF (k=60). Six follow-up packets after atlas PR #61 merges."
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

**Approved** by Sergio on 2026-10-10 at 23:08 BST, with the recommended answers to all three open questions: restricted pages left out of mesh results with no v1 override; strict resolver, with the 11 short-form links fixed by one small PR per store; packets MA, MB, MC and MF authorised now, MD and ME after MB and MC are reviewed. Not implemented yet; implementation starts after atlas PR #61 merges. Plan: [2026-10-10-atlas-mesh-level-index](../autogenesis/plans/2026-10-10-atlas-mesh-level-index.md). Base: atlas PR #61 (`feat/graph-query-drivers`, head `57198e4`, not merged). Packets land as follow-up PRs after PR #61 merges.

## Outcome in one line

Structure-only mesh graph plus federated tiered-RRF recall, opt-in by `--scope mesh`, promoted only if the multi-Atlas benchmark meets its pre-registered criteria.
