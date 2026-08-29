---
type: work
title: "Task — pointer to remote translation"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "At mount: pointer → atlas-id → matching auth alias → git remote. One function, used by mount only."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-mount-resolve.md
    kind: implements
  - path: work/mesh-mvp/f-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-auth-backends.md
    kind: related
---

## Scope

Join identity and auth so mount does not invent a second login path. If credentials are missing, mount runs the auth flow itself, then continues. Compile and query never authenticate.

## Status

designed
---
