---
type: lesson
title: "APM 0.30.0 lockfiles record git coordinates for marketplace plugins"
created: 2026-09-10
status: alive
kva: alive
work_id: 2026-09-10-atlas-marketplace-rename
description: "apm audit --ci and --frozen look for _marketplace/atlas/<pkg> and fail. Replay with a normal install or apm lock."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: derived_from
  - path: lessons/2026-09-10-register-marketplace-as-atlas.md
    kind: related
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
---

## Content

APM **0.30.0** lockfiles record **git coordinates** for marketplace plugins,
not only catalog name/version.

**Do**

- After registering `atlas` and installing `pkg@atlas`, replay with a normal
  `apm install` or run `apm lock` so lockfiles match the new coordinates.
- Expect frozen CI to look under `_marketplace/atlas/<pkg>`.

**Avoid**

- Treating `apm audit --ci` / `--frozen` failures after the rename as a missing
  package. They fail until the lockfile is replayed against catalog `atlas`.
