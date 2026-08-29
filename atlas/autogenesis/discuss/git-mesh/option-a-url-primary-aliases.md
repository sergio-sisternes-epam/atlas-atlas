---
type: document
title: "Option A — URL is primary, short aliases optional"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: alternative
description: "Agent lean, not a pin. Resolve atlas://short-name via mesh alias table, else treat token as URL."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/option-b-short-primary.md
    kind: counters
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Primary identity is the normalised git URL (or `url#subpath` for monorepos). Short names are optional `aliases` on the same mesh entry.

`atlas://skill-memory/...` still works if that alias is registered. Consumers resolve aliases through the active mesh, then fall back to treating the token as a URL.

Optional cute aliases are rejected for MVP (`drop-aliases-mvp.md`). The URL-as-primary half survives only as scheme-free host/path (option C lean), not as a nickname table.
