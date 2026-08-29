---
type: document
title: "Orbit — pointer to an Atlas that is not mounted"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "resolve vs compile vs query when atlas:// names an id that is not in the mesh."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-uri-id-extract-mvp.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-unresolved-id-policy.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Proposed lean (not pinned)

An `atlas://` id that is not in the local mesh is a **known absence**, not a corrupt page.

- `atlas resolve` — hard fail. There is no local file.
- `atlas query` — do not search that store; do not auto-mount. Say the id is not mounted.
- `atlas compile` — **warning**, not a failed compile. Pages may cite stores the author has not mounted. Today’s validator already skips `atlas://`; keep that as warn-once-per-id rather than silent skip if we can.
- `atlas mount` — the repair. Auth + clone/submodule as already pinned.

No implicit mount on compile or query. Headless mode never mounts; unresolved stays unresolved.
---
