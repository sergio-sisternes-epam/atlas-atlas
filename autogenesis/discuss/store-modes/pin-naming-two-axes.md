---
type: document
title: "Pin — Embedded stays the skill subpath; storage strategy is dedicated vs shared"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Do not reuse Embedded for the atlas branch. Storage strategy names: dedicated (own git repo) and shared (atlas branch on the consumer)."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-name-collision.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: keep **Embedded** as the `references/atlas` skill mount. Do not use that word for the consumer `atlas` branch.

Storage strategy is a second axis:

- **dedicated** — a separate git repository hosts the Atlas.
- **shared** — an isolated git branch named `atlas` on the current repository hosts the knowledge graph.

The identity pin still applies to **shared**: `atlas_id` is the consumer repo, `ref` is `atlas`, mount is a same-repo submodule.

Dedicated keeps a distinct `atlas_id` for that store repository.

The original Enter phrase "default Embedded" is now ambiguous. It must be remapped onto this axis before setup-path design.

## Provenance

Operator reply after the name-collision ask. Alive package-shape pin kept for the subpath sense.
