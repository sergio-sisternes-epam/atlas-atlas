---
type: protostar
title: "Who owns submodule add and worktree add?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: tension
description: "Mount lifecycle: CLI, agent, or human. Parent .gitmodules hygiene. Compile behaviour when a mount is missing."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/tension-checkout-lifecycle.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: related
---

## Growth path

Specify the actor for `git submodule add` / `git worktree add`, how the parent repo stays clean, and whether `atlas compile` hard-fails on a missing or wrong-commit mount.

## Open question

Reframed under T2 (`tension-checkout-lifecycle.md`). Worktree-as-write is no longer the lean. Open question is now: `atlas checkout` + submodule + PR, including parent `.gitmodules` and missing-tree behaviour.

## Origin

Mount model node. Conversation tension 2.
