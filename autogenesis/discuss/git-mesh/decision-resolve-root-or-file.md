---
type: decision
title: "resolve maps id to root and page pointer to file"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "One command. Shape of the pointer chooses directory vs file. Id-only is the git mount root."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mesh-pull.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-unresolved-id.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

`atlas resolve` is one command. What it prints depends on the pointer.

- Pointer is only an atlas-id (`github.com/sergio-sisternes-epam/atlas-atlas` or `atlas://github.com/sergio-sisternes-epam/atlas-atlas` with no further path) → the **mount root**, which is the git working copy: `.atlas/host/org/repo/`. That is the folder for ordinary git.
- Pointer includes an in-store path (`atlas://github.com/sergio-sisternes-epam/atlas-atlas/decisions/foo.md`) → that **file**: mount root + mesh `subpath` + in-store path.
- Not mounted → hard fail (already pinned).

The mesh still records the default ref for the first `mount` and for remount-when-empty. Updates after that are git in the directory `resolve` returned for the id.

OKF root without a filename is mount root + `subpath`. It is not a third resolve mode; join those two known pieces when compile or query needs the store root.
---
