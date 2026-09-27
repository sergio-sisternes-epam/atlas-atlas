---
type: experience
title: "Hub — git-backed version links and live-tree pruning"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: checkpointed
kva: alive
reality: current
description: "discussion_root on atlas-atlas. Checkpointed 2026-09-27. Claim B pinned (#37); Claim A accepted with grain opens (#38); shared relates_to.ref time-travel decision."
tags: [hub, discussion-root, git, kva, versions, checkpoint]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-aggressive-terminate-then-measure.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-delete-means-tip-search-exclusion.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: glossary.md
    kind: related
---

## Context

Subject: Atlas support for git-ref relationships to past versions of the same page, and using those refs to delete KVA-terminated notes from the live tree while keeping a pointer to the pre-delete commit.

Objective: Decide whether (and how) Atlas should treat Git history as the durability layer for superseded or terminated knowledge, so HEAD stays navigable without pretending pages are file-immutable.

This page is `discussion_root`. It does not move. Store for this orbit: atlas-atlas (not discuss-atlas).

## What happened

2026-09-27 — Sergio opened this orbit and directed that the fabric live on atlas-atlas. An accidental first pin on discuss-atlas was reverted and that store was unmounted from the steward host. Index-improvement PR work on Atlas was acknowledged and set aside.

2026-09-27 — Checkpoint constellation filed. Claim B pinned as durable decision + [atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37). Claim A accepted as durable decision with grain opens + [atlas#38](https://github.com/sergio-sisternes-epam/atlas/issues/38). Shared `relates_to.ref` time-travel decision cross-links both.

## Checkpoint (current)

- [Constellation 2026-09-27](constellation-2026-09-27-git-backed-versions.md) (synonym: checkpoint)
- [Decision — Claim B](decision-claim-b-tip-summary-git-history.md) — [atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37)
- [Decision — Claim A](decision-claim-a-living-version-hints.md) — [atlas#38](https://github.com/sergio-sisternes-epam/atlas/issues/38)
- [Decision — relates_to.ref time travel](decision-relates-to-ref-time-travel.md)

## Settled adjacent (not this orbit)

- Discuss process elsewhere still says exit stubs are not deleted by default.
- Prior discuss probe: reactivation is a new ref, not an in-place unmute.

## Batch on the hub

1. Claim A — **accepted** (grain opens deferred) → claim-a-version-hints-on-living-pages.md / decision-claim-a-living-version-hints.md / #38
2. Claim B — **pinned** → claim-b-summary-on-head-trial-in-git.md / decision-claim-b-tip-summary-git-history.md / #37
3. Counter — path stability / broken `atlas://` links — addressed by inbound rewrite + summary stand-in
4. Counter — scar readability — addressed by tip summary (not SHA-only)
5. Probe — pointer shape — **superseded** (front-matter `ref`) → open-pointer-shape.md

## Outcome

Orbit checkpointed. Standing: thesis + Claim B pins + dual need + aggressive-then-measure. Still open: Claim A grain, measure names, recall UX, optional ref compile, multiverse shared-page edges.
