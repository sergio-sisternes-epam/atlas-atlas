---
type: work
title: "Epic — Atlas storage-mesh MVP"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
work_level: epic
status: parked
kva: alive
description: "Implement pinned git storage mesh only. Query engines, nested-group URIs, APM hooks, aliases out of scope."
origin: user
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: derived_from
  - path: work/mesh-mvp/f-identity-pointers.md
    kind: related
  - path: work/mesh-mvp/f-auth.md
    kind: related
  - path: work/mesh-mvp/f-mount-resolve.md
    kind: related
  - path: work/mesh-mvp/f-verbs-modes.md
    kind: related
  - path: work/mesh-mvp/f-package-shapes.md
    kind: related
  - path: autogenesis/experiences/2026-08-29-implement-storage-mesh-mvp.md
    kind: related
---

## Scope

**Caption.** Build Atlas as a library of git-backed notebooks: name a store, log in, mount it on disk, find a root or a file, check the pages. Git moves history. APM is not part of this epic.

**In scope.** Features and tasks under `work/mesh-mvp/`. Decisions listed on those children.

**Out of scope.** Query engine internals; `install` / `checkout` / `sync` / `--target-skill`; cute aliases; APM hooks; GitLab nested-group URI width; org/repo migration; auto-mount; `reset --hard`; discuss skill narration (already shipped 0.3.5).

## Status

implementing — CLI verbs landed. Tasks marked done. Live private-remote mount not exercised in this pass.

## Outcomes

Atlas CLI 0.8.0: `id`, `auth`, `mount`, `resolve`, `atlas-mesh.json`, compile warn on unknown `atlas://`. Memory: `autogenesis/experiences/2026-08-29-implement-storage-mesh-mvp.md`.

2026-08-30: operator notes from the skill `references/mesh/` promoted into this store (`decisions/package-shapes.md`, `recipes/`).

## Related

Lineage discussion hub: `work/2026-08-26-atlas-modular-graph-protocol.md`.
---
