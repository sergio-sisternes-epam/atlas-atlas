---
type: work
title: "Task — resolve root or file"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "Id → mount root. Page URI → file with subpath. Unmounted → fail."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-mount-resolve.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-unresolved-id.md
    kind: related
---

## Scope

`resolve` prints a filesystem path. An id-only pointer prints the git mount root. A page URI prints the file after mesh subpath is applied. If that store is not mounted, fail. Do not clone as a side effect.

## Status

designed
---
