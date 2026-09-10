---
type: document
title: "Pin — atlas-mesh.json carries explicit strategy"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Each store row names strategy shared or dedicated. Do not infer mode from id and ref alone."
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
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: `atlas-mesh.json` store rows gain an explicit **`strategy`**: `shared` or `dedicated`.

Agents must not infer mode only from `id` plus `ref`.

Consequence not separately asked: today's mesh files have no such field. Until they are rewritten, a missing `strategy` is **dedicated**. A present `strategy` that contradicts the identity pin is a fail-closed mesh error.

Init writes the field. Migrate rewrites it when moving dedicated ↔ shared.

## Provenance

Operator choice on the setup-path orbit, item 2.
