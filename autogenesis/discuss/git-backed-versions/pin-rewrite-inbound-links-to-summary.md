---
type: experience
title: "Pin — rewrite living links onto the terminate summary"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "Follow-up before claim A. When the whole failed path leaves tip, every existing tip relationship that pointed at a killed page must be updated to point at the only active page left behind — the terminate summary."
tags: [prune, links, rewrite, pin, claim-b, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
---

## Context

Sergio follow-up (2026-09-27), before moving to claim A: all existing relationships to pages we are killing should be updated to point at the only active page left behind (the short terminate summary).

## What happened

### Pin

When prune removes the whole failed path from tip:

1. Find tip pages (outside the prune set) whose `relates_to` (or equivalent) still name a killed path.
2. Rewrite those edges so `path` becomes the terminate-summary page that remains on tip.
3. Tip compile stays green: no living edge should still name a path that left HEAD.

### Optional detail — closed

Do **not** put `ref` on every inbound rewrite. Tip edges only retarget to the summary. History lives on the summary’s own `ref` edges (pin-single-summary-stand-in.md).

### Why

Otherwise tip would keep dangling tip links after prune, or compile would fail. The summary is the sole live stand-in for the dead frame.

## Outcome

Inbound tip-link rewrite onto the summary is required. No `ref` on those rewritten edges. History gateway is the summary alone.
