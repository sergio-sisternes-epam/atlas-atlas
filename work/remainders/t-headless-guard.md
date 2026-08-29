---
type: work
title: "Task — headless git guard on mount and auth login"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-remainders
work_level: task
status: done
kva: alive
description: "No git on PATH → mount/auth login fail with the capability-matrix message."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-remainders.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-capabilities-by-mode.md
    kind: related
---

## Scope

Detect `git`. If missing, do not attempt clone. `compile`/`query` stay allowed.

## Status

designed
---
