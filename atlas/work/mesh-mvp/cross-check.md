---
type: document
title: "Cross-check — mesh MVP plan vs discuss pins"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: settled
kva: alive
description: "No pin-vs-task contradictions. Small coverage holes listed."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: related
---

## Method

Compare fifteen `decision-*` pages and the third consolidate snapshot to epic scope plus five features and ten tasks.

## Contradictions

None between a pinned decision and a planned task. Mount is mount, not install or checkout. Path is nested, not kebab. Parent git is submodule. Update is git, not `atlas sync`. Aliases stay out.

## Coverage holes (closed in the plan)

1. Translation — `t-translation-engine.md` linked to pointer-vs-auth and atlas-auth.
2. Git-as-update — `t-git-update.md` linked to mesh-pull, resolve, verbs.
3. No-alias — identity feature and normaliser task linked to `drop-aliases-mvp`.
4. Mesh file — `t-mesh-file.md` linked to `mesh-on-disk.md`.

Env PAT vs gh order inside one alias remains forming and off the epic.

## Explicitly deferred (must stay off the epic)

Nested-group URI width. Repo/org migration. APM-copy-then-mount. Several Atlas roots in one repo. `atlas sync`. `--target-skill`. Query engine.
---
