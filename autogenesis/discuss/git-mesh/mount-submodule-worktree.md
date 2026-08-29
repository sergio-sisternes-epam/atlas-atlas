---
type: document
title: "Mount model — submodule read, worktree write"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Storage overlay thesis. Lifecycle details parked as leaves."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

When knowledge is needed (read): check the repo out as a git submodule under `.agents/atlas/<repo>` and treat that checkout as read-only.

When knowledge must be written: earlier sketch was a worktree. Later user design (`checkout-resolve-design.md`) uses the submodule itself plus a PR. Worktree is not the MVP contribution path unless revived.

Access in today's mesh (`read` vs `read/write`) would be enforced by mount type rather than only by a field.

Related existing overlay vocabulary lives in agent-brain (`.agents/agent-brain/<id>/` project overlay vs skill `references/`). That lineage is consult-only; it is not copied here.

Open leaves from this node: submodule/worktree lifecycle, `.agents/atlas/` location semantics.
