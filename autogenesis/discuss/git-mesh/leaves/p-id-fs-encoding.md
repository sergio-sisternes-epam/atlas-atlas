---
type: protostar
title: "How is host/path atlas-id encoded as a local directory?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "github.com/Org/Repo contains slashes. Mount path under .agents/atlas/ needs a reversible encoding."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/id-to-checkout-join.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: related
---

## Growth path

Choose a reversible encoding (nested dirs, `--` flatten, or URL-quote) so mesh `root` and atlas-id stay 1:1.

## Open question

Is `.agents/atlas/github.com/Org/Repo/` acceptable (nested), or must the mount be a single directory name?

## Origin

T1 checkout-join questions after dropping aliases.
