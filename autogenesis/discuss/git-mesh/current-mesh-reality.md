---
type: document
title: "Existing mesh and atlas:// surface"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "What already ships: mesh fragments, mesh.json, contribution.repository, atlas:// skip in validate and Cartograph."
origin: internal
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: follows
  - path: decisions/cartograph-fork-in-atlas.md
    kind: backed_by
  - path: experiences/2026-08-23-implement-atlas-phase5.md
    kind: backed_by
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Already implemented in the Atlas skill:

- Mesh fragments under `mesh/fragments/` (and several filename aliases) consolidate in `atlas compile` / `validate` into root `mesh.json`.
- Required entry fields: `id`, `root`, `access` (`read` | `read/write`).
- Optional `contribution.type` and `contribution.repository` (git URL).
- Same `id` with differing `root` or `access` is a mesh conflict (hard fail).
- Validator does not filesystem-resolve targets that start with `atlas://` (same as http/https).
- Cartograph resolves `atlas://<atlas-id>/<path>` via the consolidated mesh.

Short logical ids (`skill-memory`, `project-reqs`) are still the primary `id` today. The git URL is only an optional contribution field. That is the gap the identity thesis wants to close.
