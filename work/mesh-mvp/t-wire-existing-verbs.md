---
type: work
title: "Task — wire init query compile"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: task
status: done
kva: alive
description: "init creates a store. query skips unmounted ids. compile warns per unknown atlas://."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/mesh-mvp/f-verbs-modes.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-agent-verbs.md
    kind: related
---

## Scope

Keep the existing `init`, `query`, and `compile` commands. Teach them the mesh rules: query does not walk an unmounted id; compile warns once per unknown `atlas://` and still succeeds. Do not replace the search engine.

## Status

designed
---
