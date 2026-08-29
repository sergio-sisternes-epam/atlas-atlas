---
type: decision
title: "Unmounted atlas:// is a known absence — resolve fails, compile warns"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "No auto-mount. resolve hard-fails. query skips. compile warns. mount is the repair."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/unresolved-id.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-unresolved-id-policy.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

An `atlas://` id that is not in the local mesh is a known absence.

- `atlas resolve` — hard fail.
- `atlas query` — do not search that store; do not auto-mount; report that the id is not mounted.
- `atlas compile` — warning per unknown id, not a failed compile.
- `atlas mount` — the repair (auth + clone or submodule).
- No implicit mount on compile or query.
- Headless: no mount; unresolved stays unresolved.

## Alternatives considered

- Compile hard-fail on unknown `atlas://` — rejected; citations may outrun the local working set.
- Auto-mount on resolve/query — rejected; mount stays explicit.
---
