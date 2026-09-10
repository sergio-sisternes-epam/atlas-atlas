---
type: protostar
title: "Self-hosted git cannot apply the mandatory no-direct-push ruleset"
created: "2026-09-10"
work_id: "2026-09-10-atlas-store-modes"
status: settled
kva: forming
growth: true
star_kind: tension
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
description: "GitHub makes no direct push to atlas mandatory. Shared mode on self-hosted git has no equivalent API."
relates_to:
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-self-hosted-warn.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Pending

Decide whether shared setup on a non-GitHub remote fails closed, warns and continues, or requires the operator to attest that branch protection exists.

## Origin

GitHub-driver pin: mandatory ruleset on GitHub, common git process everywhere.
