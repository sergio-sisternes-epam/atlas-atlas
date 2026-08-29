---
type: recipe
title: "Atlas capabilities by git mode"
created: 2026-08-30
description: "What compile, mount, commit, and push may do on remote git, local git, or headless."
origin: derived
sensitivity: internal
kva: alive
work_id: 2026-08-29-atlas-storage-mesh-mvp
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/atlas-capabilities-by-mode.md
    kind: follows
  - path: recipes/git-update-mounted-store.md
    kind: related
---

## Content

| Capability | Remote git | Local git | Headless |
|------------|:----------:|:---------:|:--------:|
| compile / query | yes | yes | yes |
| edit in place | yes | yes | yes, no history |
| `atlas mount` / `atlas auth` | yes | mount yes, push no | no |
| commit | yes | yes | no |
| push / PR | yes | no until a remote exists | no |

Update a mounted store with git in the folder `atlas resolve <id>` prints. Headless is reader plus edit-in-place on a folder you already have — not mount, not publish.
