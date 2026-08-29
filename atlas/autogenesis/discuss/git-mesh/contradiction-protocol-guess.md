---
type: document
title: "Contradiction 2 — never guess protocol vs reconstruct clone URL"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Closed. Pin is decision-pointer-vs-auth.md."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-storage-mesh.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: related
---

## The fight

Side A: Atlas must not invent `https` vs `ssh`. The user (or a manifest) passes a real git URL.

Side B: An APM-like `AuthResolver` rebuilds a clone URL from atlas-id + preferred protocol so install can be non-interactive.

Both cannot be the install path.

## User refinement (current lean)

See `pointer-vs-auth.md`. MD links are pointers. `atlas auth` registers an alias. Translation engine turns pointer → authenticated remote. Not pinned until you say pin.

## Current reality vs alternative

Current lean: pointer ≠ auth.
Alternative not taken: paste scheme on every install; no stored alias.
