---
type: work
title: "Task — mount reads auth.json"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-remainders
work_level: task
status: done
kva: alive
description: "Translation uses recorded host/org backend (ssh vs https). Still no PAT in the file."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-remainders.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: related
---

## Scope

If `auth.json` has ssh for that host (org override wins when present), mount uses `git@`. Otherwise HTTPS. Tokens still come from env/`gh` at runtime, never from the file.

## Status

designed
---
