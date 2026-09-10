---
type: document
title: "Pin — setup extends path init with strategy; GitHub driver is post-git"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "No new setup path. init gains strategy shared|dedicated. GitHub rulesets run after the common git process."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/setup-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/p-setup-path.md
    kind: follows
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: related
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: do not add a new Atlas path named setup.

Path **init** gains a storage **strategy**: `shared` (default) or `dedicated`.

Init still requires an existing git remote and never creates the host repository. For shared, that remote is the consumer. Init creates or reuses branch `atlas`, scaffolds SCHEMA there, and registers the same-repo submodule.

The GitHub driver is a **post-git** step inside that path when the host is GitHub. It does not replace init. Self-hosted skips the driver and warns.

Dedicated init stays "existing separate store remote", strategy opt-in.

## Provenance

Operator choice on the setup-path orbit.
