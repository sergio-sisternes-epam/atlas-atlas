---
type: experience
title: "Pin — drop the whole failed path; keep a short summary"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "User pin on prune grain. After KVA terminate, remove the whole failed path from the active tip. Keep a small summary of the memory or experience and why it ended. Use relates_to ref edges to explore the old pages in git later."
tags: [prune, pin, claim-b, whole-path, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
---

## Context

Sergio (2026-09-27), in plain terms: drop the whole failed path. Keep a small summary of the memories or experience and why that happened. The `ref` on `relates_to` lets us explore that fabric back in the future.

## What happened

### Pin

1. **Leave tip:** the entire failed path (killed thesis and the pages that existed only for that failed frame — counters, probes, exclusive side notes).
2. **Stay on tip:** a small summary node — what the experience was, what we learned or decided, and why the path ended.
3. **Bridge:** from that summary, `relates_to` entries with `ref` pointing at the old paths at the pre-prune commit (not compiled for now).

### Follow-up pin

Living tip edges that pointed at killed pages must be rewritten to the summary (pin-rewrite-inbound-links-to-summary.md).

### Not this pin

- Shared pages still useful to living ideas should not be swept away with a dead frame (exclusive-to-frame reading of “whole failed path”).
- Claim A (version hints on living pages) still open.

## Outcome

Prune grain pinned for this orbit: whole failed path off tip; short summary on tip; history via `ref`.
