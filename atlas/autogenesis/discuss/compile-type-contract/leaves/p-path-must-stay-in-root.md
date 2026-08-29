---
type: protostar
title: "compile --path must resolve inside the atlas root"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-focus-lenses
status: open
kva: forming
growth: true
star_kind: probe
origin: derived
sensitivity: internal
description: "Pinned in design: escape via .. or absolute path is critical. Implement must resolve then reject outside root."
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-compile-focus-lenses.md
    kind: derived_from
  - path: work/2026-08-27-atlas-compile-focus-lenses.md
    kind: implements
---

## Pending

`--path ../../secrets` and `--path /etc` must not walk files outside `--root`. Missing prefix inside the store is also critical (cannot focus a subgraph that is not there).
