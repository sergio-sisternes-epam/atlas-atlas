---
type: recipe
title: "Republish Atlas marketplace dependents in dep order"
created: 2026-09-10
description: "After catalog identity atlas: publish atlas 0.11.2, then discuss 0.3.10, then autogenesis 0.4.3, then atlas-cartograph 0.4.1 (atlas@atlas). okf and think still have no marketplace deps."
origin: derived
sensitivity: internal
kva: alive
work_id: 2026-09-10-atlas-marketplace-rename
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: derived_from
  - path: experiences/2026-09-10-atlas-cartograph-0.4.1-atlas-dep.md
    kind: related
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
5. **atlas-cartograph 0.4.1** — [atlas-cartograph#14](https://github.com/sergio-sisternes-epam/atlas-cartograph/pull/14)
   peeled merge `961297c0b88a65473e8922fe14aee937d481c059`, tag `v0.4.1`
   (tag object `41ad03d` — never pin tag objects). Dep `atlas@atlas`.
   Catalog pin marketplace PR 18 (`763b9b5`). 0.4.0 had `dependencies: {}`;
   this is a follow-up on the same catalog, not a second marketplace.
   `apm install atlas-cartograph@atlas` pulls atlas 0.11.2 `579e809` and
   okf 0.2.1 `5246f7b`.

Packages that declare `marketplace: atlas`: **atlas** (`okf@atlas`),
**discuss** (`atlas@atlas`), **atlas-cartograph** (`atlas@atlas`),
**autogenesis** (atlas/okf/discuss/think `@atlas`).

No marketplace deps (publish independently): **okf**, **think**.

Current catalog pins (peeled commits):

| package | version | peeled commit |
|---|---|---|
| okf | 0.2.1 | `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| atlas | 0.11.2 | `579e8090273ce991ea0717abed0775dc03f28de2` |
| discuss | 0.3.10 | `c1c0936d9a0346dce7d877646046c918de335d69` |
| think | 0.1.0 | `874613a67018c74ee95f857416fb315d2f80b92b` |
| atlas-cartograph | 0.4.1 | `961297c0b88a65473e8922fe14aee937d481c059` |
| autogenesis | 0.4.3 | `b6d8556e183c78cc0293feaa096e0db3b0cbdc01` |
