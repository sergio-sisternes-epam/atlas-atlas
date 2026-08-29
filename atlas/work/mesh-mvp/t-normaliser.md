---
type: work
title: "Task — deterministic id normaliser"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "Pure function pointer → host/org/repo or error."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-identity-pointers.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: related
---

## Scope

Implement the ordered algorithm on the decision page. Fail closed. No network. Do not add a nickname table (`drop-aliases-mvp`).

## Status

designed
---
