---
type: decision
title: "Mount runs auth; interactive login only on a real terminal"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Mount reuses gh/env/ssh, then interactive login if stdin is a terminal. Otherwise fail clearly."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/mesh-on-disk.md
    kind: related
  - path: work/mesh-mvp/t-translation-engine.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

`atlas mount` authenticates as part of the same command.

Order: reuse existing `gh` / env PAT / ssh-agent; then, if still needed and stdin is a real terminal, run the normal login (`gh auth login` or ask for a token). If there is no terminal (agent, CI), stop with a clear error that names `atlas auth login --host …`.

Compile and query never start this flow. Project `atlas-mesh.json` never stores tokens.
---
