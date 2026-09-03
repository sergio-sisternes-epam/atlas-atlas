---
type: recipe
title: "Update a mounted Atlas with git, not atlas sync"
created: 2026-08-30
description: "cd to atlas resolve <id>, then fetch/commit/push. Mesh row ref is the branch mount recorded."
origin: derived
sensitivity: internal
kva: alive
work_id: 2026-08-29-atlas-storage-mesh-mvp
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: work/mesh-mvp/t-git-update.md
    kind: follows
  - path: decisions/package-shapes.md
    kind: related
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: recipes/capabilities-by-git-mode.md
    kind: related
---

## Content

There is no `atlas sync`. Git is the overlay.

```text
cd "$(python3 scripts/atlas.py resolve github.com/org/repo)"
git fetch
git pull
git commit
git push
```

The mesh row `ref` is the branch `mount` recorded. Resolve prints `<git-root>/.atlas/<encoded-id>/`, which is the compile/query root and a parent git submodule. After a store commit and push, the parent records the new gitlink (`git add .atlas/<encoded-id>`). There is still no `atlas sync`.
