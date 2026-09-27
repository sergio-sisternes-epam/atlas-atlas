---
type: document
title: "Constellation 2026-09-27 — git-backed versions checkpoint"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: current
kva: alive
reality: current
consolidation: true
synonym: checkpoint
description: "Checkpoint join of the git-backed-versions orbit. Standing: thesis + Claim B pins + dual need + aggressive-then-measure. Claim A accepted as implement memory with grain opens. GitHub atlas#37 / #38."
tags: [constellation, checkpoint, git, claim-a, claim-b, consolidation]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: restates
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: restates
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/pin-drop-whole-failed-path.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/pin-rewrite-inbound-links-to-summary.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/pin-delete-means-tip-search-exclusion.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/challenge-current-vs-history.md
    kind: expands
  - path: autogenesis/discuss/git-backed-versions/open-aggressive-terminate-then-measure.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/open-aggressive-terminate-then-measure.md
    kind: defers
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: confirms
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: defers
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: absorbs
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: absorbs
---

## Standing

### Picture

Git is the durability layer. The live tip is a cheap current projection that may prune. After KVA terminate, tip keeps one thin summary stand-in; the whole failed path leaves tip/default search; Git retains the trail. Off-tip detail is reached via optional `relates_to.ref` (git rev) — deliberate time travel, not tip compile. Living pages may use the same `ref` shape for version hints (Claim A). Store for this orbit is atlas-atlas.

Implement track: [atlas#37 Claim B](https://github.com/sergio-sisternes-epam/atlas/issues/37).

### Confirmed

- **Thesis** — Git durability; tip may prune. Restated: tip = searchable “now”; history = recoverable what/when/why.
- **Claim B pins**
  - One summary stand-in on tip.
  - Whole failed path leaves tip (exclusive-to-frame pages); shared living pages stay.
  - Inbound tip links rewrite to that summary (no `ref` on those rewritten edges).
  - Optional `relates_to.ref` on edges into history; summary is the history gateway.
  - `ref` edges are not compiled for now.
  - Delete/terminate = tip + default-search exclusion; not physical shredding.
- **Dual need** — handy current memory and a recoverable trail. Neither keep-all-searchable-tip nor git-alone-without-tip-projection survives.
- **Space/time traversal** — tip remains the cheap now; `ref` walks are as-of/why.
- **Aggressive-then-measure** — start with aggressive whole-path prune; name measures later.
- **GitHub #37** — Claim B implement issue filed and standing as the B work pointer.

### Restated (under confirmed)

Claim B in one line: tip summary + prune failed path + inbound rewrite to summary + `ref` time travel; compile ignores `ref` for now.

## Set aside

### Refuted

- **Naive keep-all-searchable tip** — stale-but-searchable tip is the live pain; rejected as the working model.
- **Physical shredding misread of delete** — terminate removes from tip/default search; Git retains bytes. Closed by pin-delete-means-tip-search-exclusion.

### Absorbed

- **open-pointer-shape** — absorbed into front-matter `ref` + not-compiled pins (and Claim B decision).
- **open-how-much-leaves-tip** — absorbed into pin-drop-whole-failed-path (whole failed path leaves tip).
- **discuss-atlas as store for this orbit** — accidental first pin reverted; fabric lives on atlas-atlas only.

## Still open

### Deferred

- **Claim A grain** — Claim A **is accepted** as a memory to implement (shared `ref` contract with B). Only grain details deferred:
  1. Same-path only, or also cross-path supersede@ref?
  2. Which `kind` for self-history?
  3. Cadence — every meaningful edit, on request, or on KVA change?
  4. How many prior refs on tip?
- **Measure names** for aggressive prune (tip size, wrong current-state hits, forced history walks for “now”, premature-restore events).
- **Recall UX polish** for expensive history walks.
- **Optional later compile** of `ref` edges (expensive mode; out of “for now”).
- **Multiverse shared-page edge cases** — alternative branches that share pages when a failed path prunes.
- **GitHub #38** — Claim A implement issue: https://github.com/sergio-sisternes-epam/atlas/issues/38 (grain opens live there).

### Gaps

Named measures not pinned yet. Minimal recall path for path@ref still design-level.

### Contradictions

None open between standing pins. Supersede ≠ terminate remains an explicit non-collapse: same `ref` shape, different recipes.
