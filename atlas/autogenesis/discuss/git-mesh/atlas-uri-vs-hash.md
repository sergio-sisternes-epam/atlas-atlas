---
type: document
title: "Orbit — atlas:// versus Markdown #"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Cross-root pointer syntax. Hash is a heading, not a subpath."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-monorepo-subpath.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-uri-fragment.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Proposed lean (not pinned)

Same Atlas root: ordinary relative Markdown / `relates_to` paths, as OKF already does.

Another Atlas: `atlas://<host>/<org>/<repo>/<in-store-path>`

The in-store path is relative to that store’s Atlas root (`mount + subpath`), not to the git root.

A `#fragment`, if present, is a **heading (or anchor) on that page**, the same job `#` already has in Markdown. It is not a subpath and not part of the atlas-id. Resolvers may ignore an unknown fragment rather than fail the page link.

`atlas://` is treated like `http://` for local resolution: do not interpret it as a file next to the current page.
---
