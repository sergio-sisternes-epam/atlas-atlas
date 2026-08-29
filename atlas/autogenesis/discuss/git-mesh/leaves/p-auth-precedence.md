---
type: protostar
title: "What token precedence does atlas auth inherit from APM?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Copy APM's chain, a subset, or a renamed ATLAS_* env family?"
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: backed_by
---

## Growth path

Decide whether Atlas calls the same env names (`GITHUB_APM_PAT`, `GITHUB_TOKEN`, `gh auth token`) or introduces `ATLAS_*` names that the helper maps onto git.

## Open question

Two stacked choices:

1. Same env names as APM vs an `ATLAS_*` family.
2. Same order as APM (env PATs, then `gh`, then credential fill) vs the original sketch (gh first, PAT fallback).

See `apm-env-outranks-gh.md`. Copying APM is not gh-default.

## Origin

atlas-auth branch.
