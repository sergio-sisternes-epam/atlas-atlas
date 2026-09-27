---
type: experience
title: "Claim A — living pages may hint at prior versions via `ref`"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: accepted
kva: alive
reality: current
description: "Accepted Claim A. Living tip pages may relate to earlier git versions via optional relates_to.ref. Grain opens deferred. Durable decision + GitHub atlas#38."
tags: [claim-a, ref, versions, accepted]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
---

## Context

Original package split claim A from claim B. Claim B (terminate: one summary on tip, whole failed path in git, inbound rewrite, `ref` not compiled) is pinned. Claim A is version hints on pages that are still alive.

## What happened

### Claim (accepted)

A living tip page may keep small pointers to prior versions of the same path (or a closely related path) using the same `relates_to` + optional `ref` shape. The tip page stays the current memory. Old wording lives in git. The edge is a hint, not a second full copy on tip.

Illustrative shape (same as B’s pointer; different use):

```yaml
relates_to:
  - path: autogenesis/discuss/example/decision.md
    kind: supersedes   # or derived_from / related — kind TBD
    ref: abcdef1       # commit where the prior wording lived at this path
```

Same compile fence as B: `ref` edges are not resolved by tip compile for now.

Durable memory: [decision-claim-a-living-version-hints.md](decision-claim-a-living-version-hints.md).  
Implement issue: [atlas#38](https://github.com/sergio-sisternes-epam/atlas/issues/38).  
Shared capability: [decision-relates-to-ref-time-travel.md](decision-relates-to-ref-time-travel.md).

### Open questions on this node (grain only)

1. Same path only, or also “this decision supersedes that old path@ref”?
2. Which `kind` for self-history (new kind vs `derived_from` / `supersedes` / `related`)?
3. When to write such a hint — every meaningful edit, only on request, or on KVA state change?
4. How many prior refs to keep on tip (one latest, a short list, unbounded)?

## Outcome

Claim A **accepted** as implementable memory. Grain/kind/cadence/count deferred on #38. Not a rejection of Claim A itself.
