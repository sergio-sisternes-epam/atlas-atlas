---
type: experience
title: "Open — how much of the trial leaves tip"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "Next open under claim B. After KVA terminate, which pages leave the active tip versus stay as live scar or living thesis. Pointer shape (edge ref, not compiled) is already pinned for off-tip targets."
tags: [prune, subgraph, claim-b, open, forming]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
---

## Context

Pins already on this orbit: terminate *summary* stays on tip; full trial may leave tip; off-tip links use `relates_to` + optional `ref`; those `ref` edges are not compiled for now.

Next open: **how much** of the trial fabric leaves the active tip.

## What happened

### Candidate grains (batch)

1. **Terminated thesis body only** — remove (or never keep) the killed claim page from tip. Counters, probes, and batch notes that still inform living work may stay, or get their own KVA later.

2. **Whole dead branch** — everything transitively under the terminated frame (thesis + counters + failed probes unique to that frame) leaves tip. Tip keeps the exit-summary node and tip-local edges with `ref` into the pre-prune commit.

3. **Agent judgment per terminate** — path `terminate` chooses a prune set; no fixed subgraph rule. Cheapest to ship; weakest for consistent tip thinness.

4. **Hybrid** — always keep exit-summary + hubs/work; always shed pages marked `kva: terminated` (and optionally their exclusive `derived_from` children); leave shared living nodes alone.

### Evaluation axes

- Tip thinness vs accidental deletion of still-useful counters
- Predictability for agents running terminate
- How many `ref` edges the summary must carry
- Interaction with multiverse (alternative branches that share pages)

### Still not this node

- Claim A (version hints on living pages)
- Optional expensive compile of `ref` edges later

## Outcome

Pinned: whole failed path leaves tip; small summary stays; explore via ref → pin-drop-whole-failed-path.md.
