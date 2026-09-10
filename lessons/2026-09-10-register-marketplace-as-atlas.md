---
type: lesson
title: "Register atlas-marketplace as name atlas; install pkg@atlas"
created: 2026-09-10
status: alive
kva: alive
work_id: 2026-09-10-atlas-marketplace-rename
description: "apm marketplace add requires --name atlas because add defaults to repo name atlas-marketplace. Never re-add apm-marketplace."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: derived_from
  - path: decisions/atlas-marketplace-identity.md
    kind: related
  - path: lessons/2026-09-10-apm-lockfile-marketplace-git-coords.md
    kind: related
---

## Content

**Do**

1. Register with
   `apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas`.
   `--name atlas` is required: `add` defaults to repo name `atlas-marketplace`.
2. Install packages as `pkg@atlas` (`okf@atlas`, `atlas@atlas`,
   `discuss@atlas`, `think@atlas`, `atlas-cartograph@atlas`,
   `autogenesis@atlas`).

**Avoid**

- `pkg@sergio-sisternes-epam`
- `pkg@atlas-marketplace`
- Re-adding `sergio-sisternes-epam/apm-marketplace`
- Re-registering the old local marketplace name `sergio-sisternes-epam`
