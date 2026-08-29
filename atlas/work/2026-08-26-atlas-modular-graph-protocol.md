---
type: work
title: "Atlas modular graph protocol — git storage mesh"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: parked
description: "Shape Atlas storage-mesh composition over git (identity, mounts, atlas://) without mixing query. Discussion fabric lives under autogenesis/discuss/git-mesh/."
origin: internal
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: related
  - path: work/atlas-agentic-integration-v1.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
---

## Scope

Design (discussion only) the storage and mesh-composition protocol for modular Atlas knowledge graphs:

- Git as distributed file-system and overlay
- Atlas identity and `atlas://` resolution
- Read mounts (submodule) vs write mounts (worktree)
- Mesh composition of multiple git-backed OKF roots

Out of scope for this work: query engines, implement of product files, APM marketplace operations.

## Status

**implementing** — conversation retrofit into a discuss graph on 2026-08-26. No product writes. Current branch is the URL-as-id tension.

## Outcomes

None yet. First pins pending review of forming leaves.

## Related

See `relates_to`. Discussion root: `autogenesis/discuss/git-mesh/hub.md`.
