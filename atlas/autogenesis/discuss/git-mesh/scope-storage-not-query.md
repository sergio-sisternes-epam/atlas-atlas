---
type: decision
title: "This discussion is storage mesh only — query is out of scope"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Pinned conversation scope. Query stays a separate concern."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/current-reality.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Decision

This discussion fabric covers storage and mesh composition over git repositories only. Query, search engines, and retrieval ranking are a separate conversation and must not be mixed into these nodes.

## Rationale

The user locked the frame explicitly: query is completely separated from storage. Mixing retrieval into mount and identity design would blur two change classes and stall pins.

## Alternatives considered

- Treat mesh + query as one protocol now — rejected for this work.
- Defer storage until a query model exists — rejected; storage identity is the blocker.

## Consequences

Pages in this folder that drift into BM25, search UX, or query APIs should be terminated or moved. Work `atlas-bm25-and-live-migration-v1` remains the query-side draft and is not this graph.
