---
type: work
title: "Task — on-disk mesh document"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "Project file listing id, subpath, default ref, mount path. No tokens, no nicknames."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-identity-pointers.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/mesh-on-disk.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: related
  - path: autogenesis/discuss/git-mesh/mesh-pull.md
    kind: related
---

## Scope

Specify and read/write `atlas-mesh.json` at the project root. Validate with JSON Schema. `mount` writes it. Manual edits are not the API.

## Status

designed
---
