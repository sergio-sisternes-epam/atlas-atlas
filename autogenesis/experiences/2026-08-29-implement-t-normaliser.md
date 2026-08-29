---
type: experience
title: "Implement t-normaliser"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: done
kva: alive
description: "First mesh-MVP task. Pure normaliser plus atlas id CLI."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: work/mesh-mvp/t-normaliser.md
    kind: related
---

Plan approved this session. First task was the id normaliser: a pure function with no git and no network.

## Changed files

- `scripts/atlas_cli/core/identity.py`
- `scripts/atlas_cli/commands/idcmd.py`
- `scripts/atlas_cli/cli.py`
- work cards and task status
---
