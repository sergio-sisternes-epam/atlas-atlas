---
type: document
title: "Pin — Embedded atlas_id is the consumer repo, ref atlas"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Embedded store identity equals the consumer git id. Mesh ref is atlas. Mount remains a same-repo submodule."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/p-identity.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: Embedded mode uses the consumer repository as `atlas_id`, with mesh `ref: atlas`.

Mount stays a git submodule. The submodule URL is that same consumer remote. The tracked branch is `atlas`. Resolve path remains `.atlas/<encoded-consumer-id>/`.

Dedicated is unchanged: a different `atlas_id` naming a separate store repository, still mounted as a submodule.

### What this forces later

Setup must create or reuse branch `atlas` on the consumer remote, then register the submodule against that branch.

Migrate Embedded ↔ Dedicated changes `atlas_id`, not only `ref`. Existing Dedicated mounts such as `github.com/sergio-sisternes-epam/atlas-atlas` do not become Embedded by renaming a branch.

One consumer repo has at most one Embedded store, because there is one `atlas` branch and one consumer id.

## Provenance

Ask on Enter, after query of the living mount and package-shape pins.
