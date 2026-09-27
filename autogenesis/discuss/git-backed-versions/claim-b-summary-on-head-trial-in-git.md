---
type: experience
title: "Claim B refined — terminate summary on HEAD; trial body in Git"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: accepted
kva: alive
reality: current
description: "Accepted Claim B. Tip keeps terminate summary; whole failed path leaves tip; inbound rewrite; relates_to.ref for history. Durable decision + GitHub atlas#37."
tags: [claim-b, kva, git, prune, summary, accepted]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
---

## Context

Sergio refined claim B (2026-09-27): the important thing is the summarised memory of what happened, not the full trial memory. The full trial can leave the active working branch. Keep the KVA terminate summary on HEAD. Point to the old path so agents can traverse back in time and across old memories for detailed experiences, accepting higher recall cost.

## What happened

### Pins (accepted → durable decision)

On HEAD after a KVA terminate:

1. **Keep** a terminate summary node (exit reason / what we learned / why the frame died). That is the cheap, live memory.
2. **Remove** the whole failed path from the active tip (exclusive-to-frame pages).
3. **Rewrite** inbound tip links that pointed at deleted pages onto that one summary.
4. **Retain** `relates_to` + optional `ref` from the summary into the pre-prune commit (not compiled for now).
5. **Delete** = tip + default-search exclusion; Git retains bytes.

Durable memory: [decision-claim-b-tip-summary-git-history.md](decision-claim-b-tip-summary-git-history.md).  
Implement issue: [atlas#37](https://github.com/sergio-sisternes-epam/atlas/issues/37).  
Shared capability: [decision-relates-to-ref-time-travel.md](decision-relates-to-ref-time-travel.md).

### Implications

- Scar readability for humans in chat still needs the summary body on HEAD, not a SHA-only tombstone.
- Default search / compile live graph stays small.
- Detail recall is an explicit, costlier step (history walk), not ambient graph noise.
- Reactivation of a killed frame still looks like a *new* forming page derived from the summary stub, with optional restore of trial pages from the pointed commit — not an unmute of the deleted trial in place.

### Closed opens on this node

- Pointer shape → front-matter `ref` (open-pointer-shape superseded).
- How much leaves tip → whole failed path (open-how-much-leaves-tip superseded).

### Still open adjacent

- Measure names for aggressive prune (open-aggressive-terminate-then-measure.md).
- Recall UX polish; optional later compile of `ref`.
- Multiverse shared-page edge cases.

## Outcome

Claim B **accepted/pinned**. Implement on #37. Checkpoint: constellation-2026-09-27-git-backed-versions.md.
