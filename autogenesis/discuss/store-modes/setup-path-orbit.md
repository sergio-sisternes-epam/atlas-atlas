---
type: document
title: "Orbit — setup activation path"
created: "2026-09-10"
status: in-discussion
kva: alive
reality: current
description: "Live branch for shaping setup. Default shared. Git common; GitHub driver after git succeeds."
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/p-setup-path.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/p-setup-path.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/hub.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-default-shared.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: autogenesis/discuss/store-modes/pin-setup-extend-init.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-mesh-strategy-field.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-shared-bootstrap.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-existing-atlas-branch.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-existing-atlas-branch.md
    kind: follows
---

## Content

Current_branch for setup-path shaping.

Pinned inputs: default **shared**; `atlas_id` is the consumer repo with `ref: atlas`; mount is a same-repo submodule; git process is common; GitHub driver runs after git succeeds; self-hosted warns.

Today path **init** already means: existing git remote, never create the host repository, then scaffold SCHEMA. Shared does not create a repository. It creates branch `atlas` on the consumer remote. That is still "remote exists".

Batch on this orbit (not yet 1-by-1):

1. Path shape — engaged: pin-setup-extend-init.md (extend init; GitHub driver post-git).
2. Mesh field — engaged: pin-mesh-strategy-field.md (explicit `strategy`; missing field means dedicated).
3. Bootstrap — engaged: pin-shared-bootstrap.md. Existing branch — engaged: pin-existing-atlas-branch.md (reuse if SCHEMA, else fail closed).

## Provenance

Operator chose to shape setup after the self-hosted pin.
