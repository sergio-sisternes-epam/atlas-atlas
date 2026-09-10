---
type: document
title: "Orbit — migrate dedicated ↔ shared"
created: "2026-09-10"
status: in-discussion
kva: alive
reality: current
description: "Live branch for mode migrate. Identity pin: atlas_id changes. Existing path migrate still means skill-internal references/atlas relocation."
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/p-migrate-path.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/p-migrate-path.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/hub.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: related
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: autogenesis/discuss/store-modes/pin-migrate-one-path.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-migrate-preserve-history.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-migrate-both-directions.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-migrate-github-driver.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-migrate-github-driver.md
    kind: related
---

## Content

Current_branch for migrate-path shaping.

Pinned inputs: shared `atlas_id` is the consumer; dedicated `atlas_id` is a separate repo; mesh `strategy` is explicit; mount stays submodule; no dual-write.

Today path **migrate** means: move one skill off `references/atlas` onto `.atlas/<id>/`. That is not dedicated ↔ shared.

Batch on this orbit:

1. Path shape — engaged: pin-migrate-one-path.md (migrate gains a mode; no rehost path).
2. History — engaged: pin-migrate-preserve-history.md (push store commits; fail closed on unrelated destination history).
3. Directions — engaged: pin-migrate-both-directions.md (one mode, card names destination strategy).

## Provenance

Operator chose to shape migrate after setup pins.
