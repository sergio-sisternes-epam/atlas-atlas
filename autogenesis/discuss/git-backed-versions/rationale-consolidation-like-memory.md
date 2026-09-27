---
type: experience
title: "Rationale — tip consolidates; Git history is the retained dimension"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "User rationale for claim B. Human-like consolidation: synthesise and extract value without retaining every trial on the live graph. Git commit history is the other dimension that still holds detail."
tags: [rationale, consolidation, git, claim-b, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: backed_by
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
---

## Context

Sergio (2026-09-27): the summary-on-HEAD / trial-in-Git approach may mimic how the human brain synthesises memories and experiences — consolidating them and extracting value without retaining everything. Retaining everything makes graph traversal and indexing complex and expensive. The advantage of Atlas-on-Git is that detail can still live in a different dimension: commit history.

## What happened

### Design intuition (forming)

- **Live tip (cheap)** — consolidated memory: summaries, terminate reasons, living thesis. Optimised for traversal, search, and compile.
- **Git history (costly but retained)** — full trial fabric: counters, dead ends, prior wording. Recoverable when deliberate recall is worth the cost.
- **Mechanism (not the metaphor)** — tip write + prune + path@commit (or equivalent) pointer. The brain analogy motivates *why* tip should stay thin; it does not define the schema.

### Counter to watch

Analogies can smuggle wrong defaults (forgetting vs deliberate archive; unconscious consolidation vs stewarded prune). Keep the contract mechanical: what stays on HEAD, what leaves, how the pointer works, who may prune.

## Outcome

Forms a rationale edge under claim B. Does not yet pin pointer shape or claim A.
