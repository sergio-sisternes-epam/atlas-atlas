---
type: document
title: "Primary atlas-id becomes the git repository URL"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: current
description: "Identity thesis. Not pinned. Tension 1 (URL ergonomics) sits on this node."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

User claim: the atlas-id should evolve to become the git repo URL.

Today the mesh uses a short local `id` plus optional `contribution.repository`. That splits identity from provenance.

Proposed evolution: the repository URL *is* the identity. Short names, if any, are aliases declared on the mesh entry that owns that URL.

This page is forming until tension 1 is settled. Agent lean recorded on option A (URL primary, aliases optional) is not a pin.
