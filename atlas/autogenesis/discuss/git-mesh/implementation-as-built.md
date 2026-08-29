---
type: document
title: "As-built — Atlas CLI 0.8.0 versus pins"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: settled
kva: alive
reality: current
description: "Honest map of shipped code to discuss pins. Gaps stay visible."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/experiences/2026-08-29-implement-storage-mesh-mvp.md
    kind: records
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: derived_from
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: related
---

## Matches the pins

- Id is `host/org/repo`. `atlas id` / `parse_pointer` peels two segments; `#` is a fragment.
- Default mount path `.atlas/host/org/repo`. `--target` overrides. Parent git → submodule; else clone.
- Dirty or wrong-branch mount refuses. Empty submodule → `update --init`.
- `atlas-mesh.json` at project root, version 1, stores[] with id/ref/path; token fields rejected.
- `resolve` id → mount root; page path → file after optional `subpath`. Missing row → fail.
- `compile` warns on `atlas://` ids not in the mesh file.
- No `install`, `checkout`, `sync`, `--target-skill`.
- Docs: `references/mesh/capabilities-by-mode.md`, `package-shapes.md`, `git-update.md`.

## Extra versus the six-verb list

- `atlas id` is a debug/normalise command. Discuss listed six verbs; this seventh is the normaliser task.

## Partial versus pins

- **Auth grain / persist.** `atlas auth` still only probes `gh` / env / ssh. No alias file, no org override.
- **Schema library.** Hand-rolled checks plus a schema file, not a jsonschema engine.
- **Query path.** CLI is `search`, store-local.
- **Live private mount** still unproven here.

Closed in this pass: `mount` writes `subpath` when `references/atlas/SCHEMA.json` exists; clone/submodule-add send `Authorization: Bearer` when a token was resolved.

## Still deferred (discuss leaves)

Nested-group URI width. Repo/org migration. APM-copy-then-mount.
---
