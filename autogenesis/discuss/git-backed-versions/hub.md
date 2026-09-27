---
type: experience
title: "Hub — git-backed version links and live-tree pruning"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: alive
reality: current
description: "discussion_root on atlas-atlas. Once Git is engaged, the live Atlas tree need not keep every past page immutable on HEAD. Explore git-ref relationships for prior versions and for KVA-terminated cleanup."
tags: [hub, discussion-root, git, kva, versions]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
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

## Settled adjacent (not this orbit)

- Discuss process elsewhere still says exit stubs are not deleted by default.
- Prior discuss probe: reactivation is a new ref, not an in-place unmute.

## Batch on the hub (not yet engaged 1-by-1)

1. Claim A — alive pages may relate to prior git versions of themselves (hints / small pointers).
2. Claim B — engaged: keep KVA terminate *summary* on HEAD; shed full trial from active branch; point at old path/commit for costly detail recall → claim-b-summary-on-head-trial-in-git.md
3. Counter — path stability / broken `atlas://` links if the file disappears from HEAD.
4. Counter — scar readability if only a SHA remains and the exit-reason body is gone from HEAD.
5. Probe — cheapest shape of the pointer (stub page at same path vs frontmatter-only edge vs `path@commit` URI).

## Outcome

Orbit open. Forming thesis follows this hub.
