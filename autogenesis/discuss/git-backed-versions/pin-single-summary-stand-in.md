---
type: experience
title: "Pin — one summary file is the only tip stand-in"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "User pin. Active tip keeps a single summary file for a terminated path. All living links that pointed at deleted trial pages are rewritten to that summary. From the summary alone, agents read why it ended and follow relates_to ref edges back into git."
tags: [prune, summary, pin, claim-b, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
---

## Context

Sergio (2026-09-27): the active branch retains only one file with the summary. All memories that pointed to terminated or deleted files are pointed to this file. From there, they can find the `relates_to` `ref` and information on why and how to traverse back.

## What happened

### Pin

1. **One tip stand-in** — after prune, the failed path leaves exactly one living page for that failure: the terminate summary.
2. **Inbound rewrite** — every tip `relates_to` that named a deleted trial page is retargeted to that summary’s `path` (no `ref` required on those rewritten edges).
3. **History gateway** — only the summary carries `ref`-qualified edges (and the why/how prose) into the pre-prune commit. Anyone who landed on the summary follows those edges when they want costly detail.

### Closes

Optional “also put `ref` on every inbound rewrite” — **no**. Keep tip edges simple; concentrate history on the summary.

## Outcome

Claim B tip contract is coherent: one summary, rewrite all inbound tip links to it, traverse back only from its `ref` edges.
