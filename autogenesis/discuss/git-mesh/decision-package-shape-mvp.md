---
type: decision
title: "MVP package shapes — embedded skill store or dedicated Atlas repo"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Two layouts. No third APM-only OKF product. One Atlas root per git repo."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/package-shape.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-package-shape.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

MVP allows exactly two shapes:

1. Embedded: git unit is the skill or project repo; `subpath` is `references/atlas` (process memory).
2. Dedicated: git unit is the Atlas; `subpath` empty; others `atlas mount` that id.

No third product type that is “APM package of OKF without being a git Atlas.” APM may copy files; mesh membership still requires mount of a git identity. Several Atlas roots in one repo remain deferred.
---
