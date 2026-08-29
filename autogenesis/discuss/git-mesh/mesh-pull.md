---
type: document
title: "Orbit — update via git; mesh records the default ref"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "No atlas pull wrapper. resolve gives the folder; git does fetch/merge. Mesh stores the default ref for mount."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-unresolved-id.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-mesh-pull.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## User lean (not pinned)

Do not invent an Atlas VCS. `atlas resolve` prints the working copy. The agent or human runs ordinary git there (`fetch`, `pull`, `checkout` of a branch).

The mesh **must** record the **default ref** used when mounting (branch name, later maybe a tag). `atlas mount` uses that ref for the first clone or submodule add. If the tree is missing, mount still clones at that ref. Update after that is git, subject to the dirty/wrong-branch refuse rules on `mount` itself.

`atlas sync` is not required for MVP.
---
