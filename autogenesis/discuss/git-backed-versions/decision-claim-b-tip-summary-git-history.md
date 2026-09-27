---
type: decision
title: "Decision — Claim B: tip terminate summary; failed path in Git history"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: pinned
kva: alive
reality: current
description: "Durable Claim B. Tip keeps one terminate summary; whole failed path leaves tip/default search; inbound tip links rewrite to the summary; history via relates_to.ref. GitHub atlas#37."
tags: [decision, claim-b, pin, git, prune, ref]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-delete-means-tip-search-exclusion.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: supersedes
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: supersedes
  - path: autogenesis/discuss/git-backed-versions/open-aggressive-terminate-then-measure.md
    kind: related
---

## Decision

**Claim B is pinned and accepted for implementation** ([atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37)).

After KVA terminate:

1. **One tip stand-in** — keep a single terminate summary page (what happened / why / how to walk back). That is the cheap live scar.
2. **Whole failed path leaves tip** — remove pages that existed only for the failed frame (thesis, exclusive counters/probes). Shared living pages stay.
3. **Inbound rewrite** — every tip `relates_to` that named a deleted trial page retargets to the summary’s path. No `ref` on those rewritten tip edges.
4. **History gateway** — only the summary carries `relates_to` edges with optional `ref` (git rev) into the pre-prune commit/paths.
5. **Compile fence** — `ref` edges are **not** resolved by tip compile for now.
6. **Delete means tip/search exclusion** — Git retains bytes; default search excludes terminated trial pages.
7. **Aggressive-then-measure** — start with this aggressive grain; name health measures later (still open on the measure node).

Shared capability with Claim A: optional `relates_to.ref` as time travel — see decision-relates-to-ref-time-travel.md.

## Rationale

Tip must stay a healthy current projection (stale-but-searchable tip is the live pain). Git already holds durability, so the full trial need not stay on HEAD. A thin why-stand-in plus inbound rewrite preserves scar readability and tip compile greenness without SHA-only tombs. Maps to KCS “Archived” (off default search, record retained), not shredding.

## Consequences

- Implement work tracked on [atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37).
- open-pointer-shape and open-how-much-leaves-tip are superseded by this decision + pins.
- Claim A grain opens remain deferred but Claim A itself is an accepted sibling memory (#38).
- Multiverse shared-page prune edge cases and measure names stay open.
