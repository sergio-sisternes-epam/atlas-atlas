---
type: experience
title: "Rename apm-marketplace to atlas-marketplace and republish Atlas catalog"
created: 2026-09-10
work_id: 2026-09-10-atlas-marketplace-rename
status: closed
description: "GitHub repo renamed; catalog name atlas; dependents republished; peeled pins recorded; APM 0.30.0 lockfiles use git coordinates."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-release-atlas-0.11.0.md
    kind: follows
  - path: decisions/atlas-marketplace-identity.md
    kind: related
  - path: lessons/2026-09-10-register-marketplace-as-atlas.md
    kind: related
  - path: lessons/2026-09-10-apm-lockfile-marketplace-git-coords.md
    kind: related
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
---

## Context

Atlas packages were published through GitHub repo
`sergio-sisternes-epam/apm-marketplace`. Consumers had registered that catalog
under local name `sergio-sisternes-epam` and installed `pkg@sergio-sisternes-epam`.
After Atlas 0.11.0, the marketplace repo was renamed and the catalog identity
was pinned to `atlas`.

## What happened

1. GitHub renamed `sergio-sisternes-epam/apm-marketplace` to
   `sergio-sisternes-epam/atlas-marketplace`. **That repo is the marketplace
   for all things Atlas.** Catalog identity `name` is `atlas` (marketplace
   identity PR 14).
2. The old local marketplace name `sergio-sisternes-epam` was unregistered. Do
   not re-add `sergio-sisternes-epam/apm-marketplace`. Packages that declared
   `marketplace: sergio-sisternes-epam` were atlas, discuss, and autogenesis;
   all now declare `marketplace: atlas`.
3. Republish used **peeled commits**, not tag objects. Never move tags.
   Sequence already completed:
   1. Catalog identity `atlas`.
   2. Atlas **0.11.2** — [atlas#26](https://github.com/sergio-sisternes-epam/atlas/pull/26)
      merge SHA `579e8090273ce991ea0717abed0775dc03f28de2`, tag `v0.11.2`;
      dep `okf@atlas`.
   3. Catalog pin atlas 0.11.2 ref `579e809` (marketplace PR 15).
   4. Discuss **0.3.10** — main `c1c0936d9a0346dce7d877646046c918de335d69`,
      tag `v0.3.10`; dep marketplace `atlas`.
   5. Catalog pin discuss 0.3.10 (marketplace PR 16, `0914e7f`).
   6. Autogenesis **0.4.3** — main `b6d8556e183c78cc0293feaa096e0db3b0cbdc01`,
      tag `v0.4.3`; deps marketplace `atlas` (atlas 0.11.2, discuss 0.3.10).
   7. Catalog pin autogenesis 0.4.3 (marketplace PR 17, `a70a3a3`).
4. okf, think, and atlas-cartograph had no marketplace deps.
5. APM 0.30.0 lockfiles record git coordinates for marketplace plugins.
   `apm audit --ci` / `--frozen` look for `_marketplace/atlas/<pkg>` and fail
   until replayed with a normal install or `apm lock`.

## Outcome

Catalog pins (peeled commits):

| package | version | peeled commit |
|---|---|---|
| okf | 0.2.1 | `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| atlas | 0.11.2 | `579e8090273ce991ea0717abed0775dc03f28de2` |
| discuss | 0.3.10 | `c1c0936d9a0346dce7d877646046c918de335d69` |
| think | 0.1.0 | `874613a67018c74ee95f857416fb315d2f80b92b` |
| atlas-cartograph | 0.4.0 | `0e391ffb530252874b5ed163a17228a471789a12` |
| autogenesis | 0.4.3 | `b6d8556e183c78cc0293feaa096e0db3b0cbdc01` |

Consumers register
`apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas`
and install `pkg@atlas` (`okf@atlas`, `atlas@atlas`, `discuss@atlas`,
`think@atlas`, `atlas-cartograph@atlas`, `autogenesis@atlas`).
