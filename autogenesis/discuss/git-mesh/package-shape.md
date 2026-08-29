---
type: document
title: "Orbit — Atlas package shape"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Two legal shapes: skill-embedded store, or a dedicated Atlas repo. Not a third APM-only product."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-package-shape.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-mono-vs-multi.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Proposed lean (not pinned)

Two shapes, both one Atlas root per git repo:

1. **Embedded.** The skill (or project) repo is the git unit. Mesh `subpath` is `references/atlas`. That folder is process memory. Other skills may write pages into it when they have it mounted.
2. **Dedicated.** The repo *is* the Atlas. `subpath` is empty. Skills stay lean and `atlas mount` that id. APM may ship a package that *contains* such a tree; it does not become an Atlas API.

There is no third product “APM package that is only OKF and is not a git Atlas.” Git remains the overlay. Multi-atlas-in-one-repo stays deferred.
---
