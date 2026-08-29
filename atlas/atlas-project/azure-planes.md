---
type: document
title: "Optional Azure planes — map, index, orchestrator"
created: 2026-08-27
description: "Git/OKF remains source of truth. Cosmos, AI Search, and Foundry IQ are derived planes."
origin: derived
sensitivity: internal
status: alive
kva: alive
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/microsoft-as-realization.md
    kind: derived_from
  - path: atlas-project/vision.md
    kind: related
  - path: autogenesis/discuss/git-mesh/scope-storage-not-query.md
    kind: related
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
---

## Content

Four planes if Azure is switched on:

| Plane | Role | Source of truth? |
|---|---|---|
| Git / OKF files | Authoritative claims | Yes |
| Cosmos graph map | Traversable projection of pages and edges | No |
| Azure AI Search index | Lexical + vector + semantic ranking | No |
| Foundry IQ knowledge base | Agentic retrieval over Atlas index and estate sources | No |

Query routing when mounts exist: local compile-green tree, then local mesh, then Search, then Foundry IQ (IQ only when the question needs non-Atlas sources or permissioned estate data).

Do not fold these adapters into work `2026-08-26-atlas-modular-graph-protocol`. That discussion pinned storage-mesh-only; query stays a separate conversation. A future Azure-adapter work_id is allowed; it is not opened here.

Gremlin is optional. Depth-1–2 `relates_to` hops may be Cosmos NoSQL plus a change-feed projector. Use Gremlin only if traversal at scale is proven.

Dual-write rule: indexers refresh projections. Only git PRs mint pages. Stale projections must not silently answer as if they were compile-green files.

## Provenance

Assumed enhancements named by the user on 2026-08-27, rewritten under the realization frame rather than as a product rivalry.
