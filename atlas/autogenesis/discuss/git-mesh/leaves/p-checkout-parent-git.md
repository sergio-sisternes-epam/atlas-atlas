---
type: protostar
title: "Which git repo owns the .atlas submodule?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: tension
description: "Submodule add requires a parent repository. Project repo vs a dedicated overlay repo vs user-global."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-agents-location.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: related
---

## Growth path

`.atlas/` as submodule only works if some parent git repo records `.gitmodules`. That parent is either the current project, a user-level overlay, or we drop “submodule” and use a plain clone.

## Open question

If the agent is not inside a git project, where does `atlas checkout` attach the submodule?

## Origin

Checkout-resolve design.
