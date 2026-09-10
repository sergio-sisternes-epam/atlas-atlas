---
type: protostar
title: "How much of Embedded setup is a GitHub driver versus generic git?"
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
description: "GitHub can create and protect an atlas branch. Self-hosted git needs a floor that still fails closed."
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Pending

Split the GitHub driver (branch create, protection, maybe rulesets) from the self-hosted fallback so Atlas does not pretend GitHub APIs exist on every remote.

## Origin

Operator ask: GitHub driver for special branching setup and protection, plus fallback instructions for a self-hosted git server.
