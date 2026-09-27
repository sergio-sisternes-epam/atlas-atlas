---
type: decision
title: "Decision — Claim A: living pages may hint prior versions via ref"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: accepted
kva: alive
reality: current
description: "Durable Claim A. Living tip pages may use relates_to.ref for prior versions. Shared contract with Claim B. Four grain opens remain. GitHub atlas#38."
tags: [decision, claim-a, ref, versions, accepted]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: related
---

## Decision

**Claim A is accepted as a memory to implement** ([atlas#38](https://github.com/sergio-sisternes-epam/atlas/issues/38)).

A living tip page may keep small pointers to prior git versions of itself (or a closely related path) using the same optional `relates_to.ref` shape as Claim B. The tip page stays the current memory. Old wording lives in git. The edge is a hint, not a second full copy on tip.

Illustrative shape (kind TBD):

```yaml
relates_to:
  - path: some/decision.md
    kind: supersedes   # or derived_from / related — open
    ref: <git-rev>
```

Same compile fence as B: tip compile does not resolve `ref` for now.

## Opens (deferred grain — not rejection)

1. Same-path only, or also cross-path “this supersedes that path@ref”?
2. Which `kind` for self-history (new kind vs `derived_from` / `supersedes` / `related`)?
3. Cadence — every meaningful edit, on request, or on KVA state change?
4. How many prior refs on tip — one latest, short list, or unbounded?

These opens live on [atlas#38](https://github.com/sergio-sisternes-epam/atlas/issues/38) and the claim-a experience page. They do **not** reopen whether Claim A exists as implementable memory.

## Rationale

Evolving facts need a handy current page without burying tip under every prior wording, while still allowing deliberate time travel for why today’s text is what it is. Sharing Claim B’s `ref` contract avoids two schemas for one space/time capability.

## Consequences

- Sibling of Claim B ([atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37)); shared capability decision-relates-to-ref-time-travel.md.
- Schema/`ref` work should land once for both issues.
- Grain/kind/cadence/count must be recorded before or in early implementation PRs.
