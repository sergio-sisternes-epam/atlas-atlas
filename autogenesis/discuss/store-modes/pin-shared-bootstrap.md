---
type: document
title: "Pin — shared init bootstraps an empty atlas branch like an empty dedicated remote"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Missing atlas branch gets a deterministic bootstrap commit, then SCHEMA templates. It is not forked from the consumer default branch."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/setup-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-setup-extend-init.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-mesh-strategy-field.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: when branch `atlas` is missing, shared init uses the same empty-remote recipe as dedicated.

Atlas creates a deterministic bootstrap commit on `atlas`, then applies init SCHEMA templates. It does not copy the consumer default-branch tree.

If `atlas` already exists, this pin does not say whether to reuse, fail, or inspect SCHEMA. That is still forming.

## Provenance

Operator choice on setup-path orbit, item 3.
