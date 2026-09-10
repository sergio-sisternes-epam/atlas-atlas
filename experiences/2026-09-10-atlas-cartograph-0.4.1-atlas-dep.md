---
type: experience
title: "atlas-cartograph 0.4.1 declares atlas@atlas"
created: 2026-09-10
work_id: 2026-09-10-atlas-marketplace-rename
status: closed
description: "Follow-up to the marketplace rename: 0.4.0 had empty deps; 0.4.1 pins atlas@atlas; catalog 0.4.1 @ 961297c."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: follows
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
  - path: decisions/atlas-marketplace-identity.md
    kind: related
---

## Context

The marketplace rename republish left atlas-cartograph **0.4.0** with
`dependencies: {}`. That was not a second marketplace. The user required an
Atlas dependency on the same catalog `atlas`.

## What happened

1. atlas-cartograph **0.4.1** — source
   [atlas-cartograph#14](https://github.com/sergio-sisternes-epam/atlas-cartograph/pull/14).
   Peeled merge SHA `961297c0b88a65473e8922fe14aee937d481c059`. Annotated tag
   `v0.4.1`; tag object `41ad03d` — never pin tag objects.
2. Manifest:
   ```yaml
   dependencies:
     apm:
       - name: atlas
         marketplace: atlas
   ```
3. Marketplace catalog PR 18 merged
   `763b9b5c78497fdee4f7d39884316f52d2f6033f`, pin 0.4.1 @ `961297c`.
4. Consumers: `apm install atlas-cartograph@atlas` pulls atlas 0.11.2
   `579e809` and okf 0.2.1 `5246f7b`.

Packages that now declare `marketplace: atlas`: atlas (`okf@atlas`), discuss
(`atlas@atlas`), atlas-cartograph (`atlas@atlas`), autogenesis
(atlas/okf/discuss/think `@atlas`). think and okf still have no marketplace
deps.

## Outcome

Current catalog pins (peeled):

| package | version | peeled |
|---|---|---|
| okf | 0.2.1 | `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| atlas | 0.11.2 | `579e8090273ce991ea0717abed0775dc03f28de2` |
| discuss | 0.3.10 | `c1c0936d9a0346dce7d877646046c918de335d69` |
| think | 0.1.0 | `874613a67018c74ee95f857416fb315d2f80b92b` |
| atlas-cartograph | 0.4.1 | `961297c0b88a65473e8922fe14aee937d481c059` |
| autogenesis | 0.4.3 | `b6d8556e183c78cc0293feaa096e0db3b0cbdc01` |
