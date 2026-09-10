---
type: protostar
title: "What is atlas_id when the store is an atlas branch of the consumer?"
created: "2026-09-10"
work_id: "2026-09-10-atlas-store-modes"
status: settled
kva: forming
growth: true
star_kind: question
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
description: "Embedded mode must pin whether store identity is the consumer git URL plus ref atlas, or a separate id."
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Pending

Decide whether Embedded uses `atlas_id = consumer host/org/repo` with `ref: atlas`, so the submodule is a same-repo checkout, or whether identity stays a distinct store id even when the git objects live on a branch of the consumer.

## Origin

Operator proposal on the store-modes hub. Mount stays submodule in both modes, so the id and the git URL must still line up for `atlas mount` and `atlas resolve`.
