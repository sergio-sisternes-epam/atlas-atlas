---
type: document
title: "Protocol is user preference — it is not part of atlas-id"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Counter to embedding a full clone URL. https / git / ssh are transport, not identity."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/option-c-derived-short.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Most git servers speak several protocols (HTTPS, `git://`, SSH). The scheme on a clone URL is usually a user or environment preference, not a property of the knowledge store.

Embedding `https://…` (or `git@…`) in the atlas-id therefore couples identity to one transport and breaks the same repo checked out another way.

User lean recorded here: the viable identity is a **scheme-free short URL** (host/path, user-friendly), with protocol chosen later by an auth/transport helper. That is closer to option C than to a full-URL option A. Arbitrary cute aliases (`skill-memory`) were not restated as required.

This is not yet a pinned decision.
