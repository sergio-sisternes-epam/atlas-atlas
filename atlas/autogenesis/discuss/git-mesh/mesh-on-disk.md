---
type: document
title: "Mesh on disk — id, subpath, default ref"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Location project root. mount writes the row and may run auth."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/mesh-pull.md
    kind: related
  - path: work/mesh-mvp/t-mesh-file.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Fields

atlas-id, optional subpath, default git ref, mount path if not the default nested path. No tokens. No nicknames.

## Confirmed

**Location:** project root, like other repo config.

**Writer:** first `atlas mount <source>` adds the mesh row. Manual edits are not expected. The file is machine-written. A git merge may still touch it; that is a conflict to resolve, not the editing API.

**Auth:** if that mount needs credentials, `mount` runs the auth flow in the same command. The user is not sent away to `atlas auth` first.

**Ref:** `mount --ref`. Omit → remote default; persist the name actually checked out, never `HEAD`. See `decision-mesh-ref.md`.

**Format:** JSON with schema. Filename `atlas-mesh.json`. See `decision-mesh-json-schema.md`.

**Inner auth:** reuse, then full login if stdin is a terminal. See `decision-mount-auth-flow.md`.

## Still open

None on this page.
---
