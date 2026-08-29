---
type: decision
title: "Mount is a submodule when the parent is a git repo"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Inside a git work tree, atlas mount adds a submodule at .atlas/host/org/repo. Otherwise a plain clone."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mount-parent-git.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-mount-nested-path.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-checkout-parent-git.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

- If `atlas mount` runs **inside a git work tree**, the target is a **git submodule** at `.atlas/<host>/<org>/<repo>/` (or `--target` inside that tree). The parent records URL and branch in `.gitmodules`. Sharing the mesh is a commit of that metadata.
- If there is **no parent git repo**, mount is a **plain clone**.
- Headless mode does not mount.

## Alternatives considered

- Nested clone + gitignore `.atlas/` — rejected as default; mesh would not travel with the project.
- User-global cache only — rejected as default; `--target` can still do that.

## Consequences

Mount lifecycle (dirty tree, wrong branch, missing submodule on clone) stays a forming leaf. Default attachment is decided.
---
