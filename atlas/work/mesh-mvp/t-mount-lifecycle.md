---
type: work
title: "Task — mount lifecycle refuse rules"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "No-op if clean right ref. Refuse dirty or wrong branch. Init empty submodule."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-mount-resolve.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: related
---

## Scope

No reset --hard. No atlas sync.

## Status

designed
---
