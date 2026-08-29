---
type: decision
title: "Mount lifecycle — refuse dirty or wrong-branch; compile ignores"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "resolve maps; mount adds or no-ops; dirty/wrong-branch refuse; empty submodule init; compile store-local."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mount-lifecycle.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-mount-submodule.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

- **Missing:** `resolve` fails; `mount` clones or `submodule add`.
- **Present, clean, right branch:** `resolve` prints the path; `mount` is a no-op success.
- **Dirty:** `resolve` prints path + warn; `mount` **refuses**. No `--force` in MVP.
- **Wrong branch:** `resolve` prints path + warn; `mount` **refuses**. No implicit checkout.
- **`.gitmodules` lists it, directory empty:** `resolve` fails; `mount` runs `submodule update --init`.
- **`compile`:** does not care about mount state. It is store-local.
- Atlas does not `reset --hard`. Publish is git inside the mounted tree.
- Fetch-from-remote update is not this verb (`sync` / mesh-pull remains a gap).

## Alternatives considered

- `--force` reset on dirty — rejected for MVP.
- Implicit branch switch — rejected.
---
