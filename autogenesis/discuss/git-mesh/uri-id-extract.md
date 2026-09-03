---
type: document
title: "How resolve peels an atlas-id out of atlas://"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Not a hunting regex. URI parse + host profile or longest-prefix against known ids."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-uri-vs-hash.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/challenge-slash-join-uri.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Content

`atlas://github.com/sergio-sisternes-epam/atlas-atlas/page.md#heading` is a normal URI. Extraction is two stages.

1. Generic URI parse (scheme, host, path segments, fragment). Not an Atlas regex.
2. Decide how many path segments belong to the id.

Stage 2 cannot be “any repo on any host” from slashes alone. GitHub is two segments; GitLab groups are not.

MVP: host profile. `github.com` / `*.ghe.com` → two segments after host. Unknown host → same two-segment default, fail if fewer.

General case later: **longest prefix** of `host + path` that equals a known atlas-id (mesh or explicit mount list). That is a dictionary lookup, not a richer regex. If nothing matches, fall back to the host profile or error.

Do not scan the page path for `tree`, `.git`, or other tokens.
---
