---
type: document
title: "Pin — new consumers default to shared storage strategy"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Setup path default is shared (atlas branch). Existing dedicated mounts stay dedicated until migrate."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-naming-two-axes.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-default-embedded.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: the setup activation path defaults to **shared** for new consumers.

Existing dedicated mounts stay dedicated until the migrate path runs. Atlas does not rewrite a live dedicated `atlas_id` as a side effect of this default.

Shared still means consumer `atlas_id`, `ref: atlas`, submodule mount.

## Provenance

Original Enter said default Embedded. Naming pin remapped that word. Operator chose default shared.
