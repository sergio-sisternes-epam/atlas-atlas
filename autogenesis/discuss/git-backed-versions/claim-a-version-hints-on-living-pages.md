---
type: experience
title: "Claim A — living pages may hint at prior versions via `ref`"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "Engaged claim A. An alive or forming page on tip may relate to earlier git versions of itself (or a named path) with optional relates_to ref, carrying a small human hint. Not the terminate-prune path; that is claim B."
tags: [claim-a, ref, versions, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
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
---

## Context

Original package split claim A from claim B. Claim B (terminate: one summary on tip, whole failed path in git, inbound rewrite, `ref` not compiled) is pinned. Claim A is version hints on pages that are still alive.

## What happened

### Claim (forming)

A living tip page may keep small pointers to prior versions of the same path (or a closely related path) using the same `relates_to` + optional `ref` shape. The tip page stays the current memory. Old wording lives in git. The edge is a hint, not a second full copy on tip.

Illustrative shape (same as B’s pointer; different use):

```yaml
relates_to:
  - path: autogenesis/discuss/example/decision.md
    kind: supersedes   # or derived_from / related — kind TBD
    ref: abcdef1       # commit where the prior wording lived at this path
```

Same compile fence as B: `ref` edges are not resolved by tip compile for now.

### Open questions on this node

1. Same path only, or also “this decision supersedes that old path@ref”?
2. Which `kind` for self-history (new kind vs `derived_from` / `supersedes` / `related`)?
3. When to write such a hint — every meaningful edit, only on request, or on KVA state change?
4. How many prior refs to keep on tip (one latest, a short list, unbounded)?

## Outcome

Claim A engaged. Awaiting pins on grain, kind, and cadence.
