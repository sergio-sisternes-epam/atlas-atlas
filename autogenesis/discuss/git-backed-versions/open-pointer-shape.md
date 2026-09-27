---
type: experience
title: "Open — pointer shape for pruned trial fabric"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: superseded
kva: surviving
reality: current
description: "Superseded. Pointer shape absorbed into front-matter ref + not-compiled pins and Claim B decision."
tags: [pointer, git, claim-b, superseded]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
---

## Context

Claim B refined: keep KVA terminate summary on HEAD; shed full trial from the active branch; retain detail in Git. Next open point: the pointer shape that makes that scar traversable.

## What happened

### Candidate shapes (batch)

1. **Same-path stub** — after prune, the original path remains a short page: exit reason, `kva: terminated`, and fields naming `prior_commit` (pre-delete SHA) plus optional `prior_paths[]`. Cheap for `atlas://` stability. Tip still has a file at that path.

2. **Summary-only node + frontmatter pointer** — terminate summary lives at a dedicated exit path (or stays on the hub/work edge). Frontmatter carries `prior_path` + `prior_commit`. Original trial paths disappear from HEAD. Links to those paths must rewrite or fail-soft to the summary.

3. **URI / ref form** — no stub body required beyond a typed relation such as `path@commit` or `atlas://…@rev/path` on `relates_to`. Maximum tip thinness. Highest demand on compile, search, and recall tooling.

### Evaluation axes

- Tip thinness
- Link stability for existing `relates_to` / `atlas://`
- Human scar readability without `git show`
- Implement cost for compile + recall

### Still not this node

- How much of the trial leaves tip (one page vs whole subgraph)
- Claim A (version hints on living pages)

## Outcome

**Superseded / absorbed.** Front-matter `ref` + not-compiled pins closed this open. See decision-claim-b-tip-summary-git-history.md, pin-candidate-frontmatter-ref.md, pin-ref-edges-not-compiled.md, and constellation-2026-09-27-git-backed-versions.md.
