---
type: document
title: "Orbit — parent git when mounting"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "If cwd is a git repo, is .atlas/host/org/repo a submodule or a nested clone?"
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-mount-nested-path.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-checkout-parent-git.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The act

`atlas mount` writes `.atlas/<host>/<org>/<repo>/`. That folder is a git working copy (git is the overlay).

Question: if the **parent** directory is already a git repo, how is the child recorded?

| Option | Effect |
|--------|--------|
| Submodule | Parent `.gitmodules` points at the Atlas remote. `git clone --recurse` gets the mesh. Dirty parent until committed. |
| Nested clone | Child has its own `.git`. Parent must gitignore `.atlas/` or it looks like untracked noise. |
| Always user-global | Never attach to the project repo. Breaks “project mesh travels with the repo.” |

## Proposed lean (not pinned)

- **Inside a git work tree:** mount as a **submodule** at `.atlas/host/org/repo`. Parent records URL + branch. Agent (or human) commits `.gitmodules` when they want the mesh shared.
- **Not inside a git work tree:** plain clone at that path (or `--target`).
- Headless: no mount (already pinned).
- Parent should `.gitignore` nothing required if submodule is used; if someone uses `--target` outside `.atlas`, their choice.

`.atlas/` at repo root is the project mesh. User-global cache is out of MVP unless `--target` points there.
