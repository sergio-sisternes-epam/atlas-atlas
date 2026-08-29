---
type: document
title: "Tension 2 — checkout lifecycle"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "T2 checkout lifecycle. current_branch moved to atlas-as-own-repo (install, own repo, git is overlay)."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-checkout-parent-git.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

T1 left with: no aliases; scheme-free host/path id; checkout URL supplied by the user; resolve does not clone.

T2 is the lifecycle of that checkout:

- Who runs `atlas checkout` (human, agent, both)
- Which parent git records the submodule
- What mesh stores (url, branch, root, id)
- What happens if the tree is missing, dirty, or on the wrong branch
- How contribution PRs work without a worktree
- Whether `atlas compile` cares about checkout state (probably no: compile is store-local)

Worktree-as-write-mount is not the current lean.
