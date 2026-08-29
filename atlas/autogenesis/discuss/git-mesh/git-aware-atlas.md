---
type: document
title: "Atlas is git-aware; git is optional but limiting"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Thesis: Atlas understands git remotes, checkouts, and worktrees. Pure-local trees still exist with reduced features."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/current-mesh-reality.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

User claim: Atlas becomes git-aware. Git is optional, but most Atlas composition features are limited without it.

Intended git roles:

- Durable identity of an Atlas root (repository URL)
- Transport (clone, fetch, submodule, worktree)
- Overlay (read-only checkout vs writable worktree)

Pure-local (no-git) Atlases remain valid OKF trees. They cannot participate in contribution, pull, or multi-machine mesh until they gain a repository.

Which exact features degrade without git is an open leaf (`leaves/p-optional-git-cut.md`).
