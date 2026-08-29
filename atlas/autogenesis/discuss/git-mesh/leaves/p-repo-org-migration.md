---
type: protostar
title: "What happens when a repo or organisation migrates?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: open
kva: forming
reality: current
growth: true
star_kind: tension
description: "Host/path ids break if the repo is renamed, transferred, or moved to another host. Out of MVP."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: related
---

## Growth path

Later: stable redirects, former-id aliases that are provenance not nicknames, or a UUID plus locator. Not in this MVP.

## Open question

If `github.com/old-org/atlas` moves to `github.com/new-org/atlas`, do existing `atlas://` edges rewrite, dual-key, or break?

## Origin

T1 identity pin (host/path, no aliases). User named the tension and deferred it.
