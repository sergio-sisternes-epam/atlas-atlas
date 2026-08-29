---
type: work
title: "Task — update and publish via git in resolve root"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "Document and smoke: cd $(atlas resolve <id>) and use git. No atlas sync."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-verbs-modes.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/mesh-pull.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-agent-verbs.md
    kind: related
---

## Scope

Agent docs plus a smoke that fetch/commit happen in the mount root. Do not add an Atlas pull command.

## Status

designed
---
