---
type: document
title: "Pin — migrate onto shared runs the GitHub driver; reverse does not strip rulesets"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "dedicated → shared applies the same post-git GitHub driver as init. shared → dedicated leaves GitHub rulesets in place unless the operator asks to remove them."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/migrate-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/p-migrate-github-driver.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-migrate-both-directions.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10:

When destination strategy is **shared** and the host is GitHub, migrate runs the same post-git GitHub driver as init: mandatory no-direct-push ruleset on `atlas`, recommended Copilot Reviews on pull requests.

When destination strategy is **dedicated**, migrate does **not** strip those rulesets from the consumer. Removal is a separate operator request, not part of migrate.

Self-hosted shared still warns and continues.

## Provenance

Leftover from the both-directions pin. Operator asked to pin it before a design Run.
