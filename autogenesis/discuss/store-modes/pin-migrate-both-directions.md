---
type: document
title: "Pin — one migrate mode, both directions, card names destination strategy"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Strategy migrate is bidirectional. Enter card names the destination strategy. Source is the current mesh strategy."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/migrate-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/migrate-path-orbit.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-migrate-preserve-history.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-mesh-strategy-field.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: strategy migrate is **both directions** in one mode.

The Enter card names the **destination** `strategy` (`shared` or `dedicated`). The source is the current mesh `strategy` (missing field means dedicated). Same source and destination is a no-op fail closed.

Dedicated destination still requires an existing remote. Shared destination uses consumer `atlas_id` and branch `atlas`, then the GitHub post-git driver when the host is GitHub.

## Provenance

Operator choice on migrate-path orbit, item 3.
