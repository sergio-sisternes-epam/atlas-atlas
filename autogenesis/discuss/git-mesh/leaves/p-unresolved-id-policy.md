---
type: protostar
title: "Missing atlas-id in the active mesh — hard error or soft external?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Compile/validate policy for atlas:// targets whose id is not in mesh.json."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/current-mesh-reality.md
    kind: derived_from
---

## Growth path

Today validate skips all `atlas://` targets. A git-aware mesh may instead hard-fail unknown ids, or keep them as unresolved externals that Cartograph can still draw.

## Open question

Is an unresolved `atlas://` a compile defect or a permitted dangling edge?

## Origin

First shaping item (formal URI scheme).
