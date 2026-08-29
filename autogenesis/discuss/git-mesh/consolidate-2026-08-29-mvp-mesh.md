---
type: document
title: "Consolidate 2026-08-29 — MVP storage mesh"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
consolidation: true
description: "Third snapshot. Pins after contradictions-closed: auth, mount path, lifecycle, URI, resolve, package, verbs."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-contradictions-closed.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
  - path: autogenesis/experiences/2026-08-29-implement-storage-mesh-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-mount-nested-path.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-mount-submodule.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-mount-lifecycle.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-uri-id-extract-mvp.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-unresolved-id.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-agent-verbs.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-capabilities-by-mode.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/where-memories-live.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/leaves/p-uri-nested-groups.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-repo-org-migration.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-apm-git-trace.md
    kind: defers
---

## Picture

A skill keeps its own notes in `references/atlas`. Shared notes live in git repositories. Atlas names a store as `github.com/org/repo`, mounts it onto disk, and lets agents find pages. Git moves history. APM only copies packages.

```text
pointer → auth alias → mount → .atlas/host/org/repo/
resolve(id) → that folder     resolve(page URI) → file
compile / query on what is already there
git in the folder for fetch, commit, PR
```

## Confirms

Pointers are not passwords. `atlas auth` holds the login. `atlas mount` puts the tree on disk. Default path is nested `.atlas/host/org/repo`. Inside a git project that folder is a submodule. Dirty or wrong branch: mount refuses. Id is a deterministic `host/org/repo`. One Atlas root per repo; extra folder is mesh `subpath`. `atlas://` is a normal URI; MVP peels two segments after the host. Unmounted links warn at compile and fail at resolve. Resolve follows the pointer (root or file). Two package shapes: notes inside a skill, or a repo that is only notes. Six Atlas verbs; git for the rest. Git is the default overlay; local git counts; headless is limited. This discussion living under `autogenesis/` on the Atlas skill store is expected.

## Indexes / defers

Nested-group URI width. Repo or org migration. APM copy then mount. Those stay forming.

## Absorbs

The gap queue items we closed after the second snapshot (auth, encoding, parent git, lifecycle, normaliser, subpath, URI, unresolved, pull, package, verbs).
---
