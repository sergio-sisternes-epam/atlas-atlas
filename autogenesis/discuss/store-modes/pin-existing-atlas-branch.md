---
type: document
title: "Pin — existing atlas branch is reused only if it is an Atlas"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "If atlas exists and has SCHEMA.json, shared init reuses it. If atlas exists without an Atlas root, fail closed."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/setup-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/p-existing-atlas-branch.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-shared-bootstrap.md
    kind: follows
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: derived_from
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10:

If branch `atlas` is missing: bootstrap empty, then templates (previous pin).

If branch `atlas` exists and the tree contains `SCHEMA.json` at the store root: **reuse**. Do not rewrite history. Register the submodule against that branch.

If branch `atlas` exists and the tree is not an Atlas root: **fail closed**. Do not delete the branch. Do not overlay SCHEMA onto product history.

## Provenance

Operator choice on the existing-atlas-branch tension.
