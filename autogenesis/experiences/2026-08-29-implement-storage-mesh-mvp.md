---
type: experience
title: "Storage-mesh MVP implemented on Atlas CLI"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: done
kva: alive
description: "id, auth, mount, resolve, atlas-mesh.json, compile warn. Lineage: discuss pins + approved plan."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-uri-id-extract-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: related
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: records
  - path: autogenesis/discuss/git-mesh/decision-mesh-json-schema.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mesh-ref.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-auth-flow.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-agent-verbs.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-unresolved-id.md
    kind: related
---

Approved plan `2026-08-29-atlas-storage-mesh-mvp` was implemented on the Atlas skill CLI (0.8.0). Behaviour follows the git-mesh discuss pins, not a parallel design.

## What shipped

- Pure `normalise` / `parse_pointer` (`atlas id`)
- `atlas-mesh.json` at project root, JSON, no token fields
- `atlas auth`, `atlas mount`, `atlas resolve`
- compile warning when `atlas://` names an id absent from the mesh file
- Docs under skill `references/mesh/`

## Changed files

- `scripts/atlas_cli/core/identity.py` `meshfile.py` `auth.py` `translate.py` `gitops.py`
- `scripts/atlas_cli/commands/idcmd.py` `mount.py` `resolve.py` `authcmd.py` `validate.py`
- `scripts/atlas_cli/cli.py` `schemas/atlas-mesh.schema.json`
- `SKILL.md` CLI list
- `references/mesh/capabilities-by-mode.md` `package-shapes.md` `git-update.md`

## Still not proven in this session

Live `mount` against a private remote. Nested-group URI width remains deferred discuss work, not this implement.
---
