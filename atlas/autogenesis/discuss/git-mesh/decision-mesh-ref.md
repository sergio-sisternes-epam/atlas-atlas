---
type: decision
title: "Mount --ref; mesh stores the real branch name"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "atlas mount --ref. Omit → remote default. Persist the name actually checked out, never HEAD."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mesh-on-disk.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: follows
  - path: work/mesh-mvp/t-mesh-file.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

- `atlas mount <source> [--ref <name>]`.
- With `--ref`, clone or submodule-add that ref and write it on the mesh row.
- Without `--ref`, use the remote’s default branch, then persist the **name actually checked out**, not `HEAD`.
- Later `mount` of the same source no-ops only if clean and on that stored ref.
- Changing the intended ref later is out of MVP.
- The ref is not part of the atlas-id and not a `#` fragment.
---
