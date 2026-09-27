---
type: experience
title: "Claim B refined — terminate summary on HEAD; trial body in Git"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "Engaged refinement of claim B. What must stay on the active branch is the summarised KVA terminate memory, not the full trial. Point at the old path/commit so detailed experiences remain traversable at higher recall cost."
tags: [claim-b, kva, git, prune, summary, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/rationale-consolidation-like-memory.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-how-much-leaves-tip.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
---

## Context

Sergio refined claim B (2026-09-27): the important thing is the summarised memory of what happened, not the full trial memory. The full trial can leave the active working branch. Keep the KVA terminate summary on HEAD. Point to the old path so agents can traverse back in time and across old memories for detailed experiences, accepting higher recall cost.

## What happened

### Pin candidate (forming)

On HEAD after a KVA terminate:

1. **Keep** a terminate summary node (exit reason / what we learned / why the frame died). That is the cheap, live memory.
2. **Remove** (or never promote) the full trial body from the active branch tip.
3. **Retain** a git-ref / path pointer from that summary to the pre-prune location so detailed pages remain reachable via history (`git show`, path@commit, or equivalent Atlas recall), at higher cost than ordinary search.

This is not “delete the scar.” It is “keep the scar thin on HEAD; put the transcript in Git.”

### Implications

- Scar readability for humans in chat still needs the summary body on HEAD, not a SHA-only tombstone.
- Default search / compile live graph stays small.
- Detail recall is an explicit, costlier step (history walk), not ambient graph noise.
- Reactivation of a killed frame still looks like a *new* forming page derived from the summary stub, with optional restore of trial pages from the pointed commit — not an unmute of the deleted trial in place.

### Support

Consolidation rationale: tip synthesises; Git history retains detail at higher cost (rationale-consolidation-like-memory.md).

### Still open on this node

- Exact pointer shape — now on open-pointer-shape.md.
- Whether “full trial” means every counter page, or only the terminated thesis body — now on open-how-much-leaves-tip.md.
- How recall APIs surface “expensive history” vs tip search.

## Outcome

Claim B is sharper. Next: pin pointer shape, or take claim A in parallel.
