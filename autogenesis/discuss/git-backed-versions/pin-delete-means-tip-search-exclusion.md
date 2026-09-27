---
type: decision
title: "Pin — Atlas ‘delete’ / terminate means tip and default-search exclusion"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: pinned
kva: surviving
reality: current
description: "In this orbit, terminate/delete removes pages from the tip projection and default search; git history retains the trail. Not physical shredding."
tags: [pin, claim-b, terminate, archive]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: related
---

## Claim

When this discussion says delete or terminate a memory from the live graph, it means: remove it from the tip tree and from default Atlas search so the current projection stays contained and healthy. Git still holds the prior bytes. Agents recover what/when/why by deliberate history walks (`ref` / as-of), not by keeping superseded pages searchable on tip.

## Why

Maps to KCS “Archived” (logically gone from search, still viewable via old links or advanced/history paths), not to shredding the record. Closes the think-challenge misread that option 2 implied physical loss.

## Still required

Every terminate still leaves a tip stand-in (summary + why) and rewrites inbound tip links to that stand-in. Without that, tip has holes and “current state” forces history walks.
