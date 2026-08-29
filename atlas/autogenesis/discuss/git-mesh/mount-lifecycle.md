---
type: document
title: "Orbit — mount lifecycle"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Dirty tree, missing submodule, wrong branch. What mount and resolve do."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/gap-queue.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-mount-submodule.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-mesh-pull.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Proposed lean (not pinned)

| State | `atlas resolve` | `atlas mount` (same pointer) | `atlas compile` |
|-------|-----------------|------------------------------|-----------------|
| Not present | fail: not mounted | clone or submodule add | ignore (store-local) |
| Present, clean, right branch | print local path | no-op success | ignore |
| Present, dirty | print path + warn | refuse unless `--force` (MVP: refuse) | ignore |
| Present, wrong branch | print path + warn | refuse; do not switch a dirty or divergent tree | ignore |
| `.gitmodules` lists it, dir empty | fail | `submodule update --init` | ignore |

Publish stays git (commit in the mounted tree, PR). Atlas does not `reset --hard`.

Update-from-remote is **`atlas sync`** (or `mount --update`) — separate from first mount. Can stay a sibling gap (#6 mesh pull).
