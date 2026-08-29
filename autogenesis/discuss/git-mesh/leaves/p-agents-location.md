---
type: protostar
title: "What is the scope of .agents/atlas/?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Per-project directory, per-user cache, or both. Relation to agent-brain overlays."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: derived_from
---

## Growth path

Decide whether `.agents/atlas/<repo>` is project-local, user-global, or a pair (cache + project overlay). Note agent-brain already uses `.agents/agent-brain/<id>/` for project overlays.

## Open question

Sibling namespace, nested under agent-brain, or a parallel cache outside the project?

## Origin

Mount model node. Conversation tension 4.
