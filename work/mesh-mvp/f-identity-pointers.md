---
type: work
title: "Feature — identity and pointers"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: feature
status: done
kva: alive
description: "Scheme-free id, normaliser, atlas:// two-segment peel, mesh subpath."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-uri-id-extract-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: related
  - path: work/mesh-mvp/t-normaliser.md
    kind: related
  - path: work/mesh-mvp/t-uri-peel.md
    kind: related
  - path: work/mesh-mvp/t-mesh-subpath.md
    kind: related
  - path: work/mesh-mvp/t-mesh-file.md
    kind: related
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: related
---

## Scope

Name a store as `host/org/repo`. Parse pointers. Record optional `subpath`. Not nested-group width.

## Status

designed
---
