---
type: document
title: "Current reality — storage mesh discussion"
created: 2026-08-26
updated: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Locked facts after MVP implement. Early .agents/worktree proposal is not current."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: related
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: related
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
---

## Content

1. Query engine design stayed out of this fabric. Lookup uses existing `atlas search` on a store root.
2. Git is the overlay. Headless degrades (no mount/push). See capability matrix.
3. Identity is scheme-free `host/org/repo`, not a full URL and not `.agents/atlas/<repo>`.
4. Mount is `.atlas/host/org/repo`, submodule if the parent is git. Worktree-as-write-mount was dropped.
5. Project catalogue is `atlas-mesh.json`. In-store mesh fragments (`mesh.fragment.json`) still exist for compile composition; they are a different file.
6. Product pins live under `autogenesis/discuss/git-mesh/decision-*.md`. Implement as-built: `implementation-as-built.md`.
7. Implement work_id: `2026-08-29-atlas-storage-mesh-mvp`. Discussion lineage: `2026-08-26-atlas-modular-graph-protocol`.
8. Skill-internal store at `<skill>/references/atlas` is superseded (2026-09-03). Living pin: `decision-mount-dot-atlas-only.md`. Activation path is `references/atlas.md`; mounts live under the active repo’s `.atlas/<encoded-id>/`.
---
