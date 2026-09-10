---
type: recipe
title: "Republish Atlas marketplace dependents in dep order"
created: 2026-09-10
description: "After catalog identity atlas: publish atlas 0.11.2, then discuss 0.3.10, then autogenesis 0.4.3. Leaf packages had no marketplace deps."
origin: derived
sensitivity: internal
kva: alive
work_id: 2026-09-10-atlas-marketplace-rename
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

Marketplace deps must republish after the catalog identity is `atlas`, in
dependency order. Pin **peeled commits**, not tag objects. Never move tags.
Leaves with no marketplace deps do not block.

1. Catalog identity `atlas` (marketplace identity PR 14).
2. **atlas 0.11.2** — [atlas#26](https://github.com/sergio-sisternes-epam/atlas/pull/26)
   merge SHA `579e8090273ce991ea0717abed0775dc03f28de2`, tag `v0.11.2`;
   dep `okf@atlas`. Catalog pin marketplace PR 15.
3. **discuss 0.3.10** — main `c1c0936d9a0346dce7d877646046c918de335d69`,
   tag `v0.3.10`; dep marketplace `atlas`. Catalog pin marketplace PR 16
   (`0914e7f`).
4. **autogenesis 0.4.3** — main `b6d8556e183c78cc0293feaa096e0db3b0cbdc01`,
   tag `v0.4.3`; deps marketplace `atlas` (atlas 0.11.2, discuss 0.3.10).
   Catalog pin marketplace PR 17 (`a70a3a3`).

No marketplace deps (publish independently): **okf**, **think**,
**atlas-cartograph**.

Catalog pins (peeled commits) for that republish:

| package | version | peeled commit |
|---|---|---|
| okf | 0.2.1 | `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| atlas | 0.11.2 | `579e8090273ce991ea0717abed0775dc03f28de2` |
| discuss | 0.3.10 | `c1c0936d9a0346dce7d877646046c918de335d69` |
| think | 0.1.0 | `874613a67018c74ee95f857416fb315d2f80b92b` |
| atlas-cartograph | 0.4.0 | `0e391ffb530252874b5ed163a17228a471789a12` |
| autogenesis | 0.4.3 | `b6d8556e183c78cc0293feaa096e0db3b0cbdc01` |
