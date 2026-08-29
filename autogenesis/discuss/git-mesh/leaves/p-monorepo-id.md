---
type: protostar
title: "How is an Atlas inside a monorepo identified?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: tension
description: "Many stores live at a subpath of a larger git repo (skill package, project monorepo)."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: related
---

## Growth path

Choose `url#path/to/atlas-root` as part of the id, or keep the id as the repo URL plus a separate `subpath` field on the mesh entry.

## Open question

Two Atlases in one git repository — one id or two?

## Origin

Identity thesis plus tension 1 monorepo question.
