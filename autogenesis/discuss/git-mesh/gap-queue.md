---
type: document
title: "Remaining gaps before next consolidate"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Queue after auth, nested path, and submodule pins. Closed leaves omitted."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-contradictions-closed.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-mount-submodule.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Closed since last snapshot

Auth grain/backends, nested `.atlas/host/org/repo`, submodule-if-parent, install/checkout naming, target-skill, git-default.

## Still open (suggested order)

1. Mount lifecycle — dirty, missing, wrong branch, uninit submodule
2. URL / id normaliser — exact string function
3. Monorepo `subpath` — one repo, several Atlas roots
4. `atlas://` vs Markdown `#`
5. Missing / unresolved id
6. Mesh pull / update already-mounted trees
7. Atlas package shape + mono vs multi
8. APM-copy then `atlas mount` (agent verbs only)
9. Agent-verb list polish (`init`, `mount`, `resolve`, `query`, `auth`)
