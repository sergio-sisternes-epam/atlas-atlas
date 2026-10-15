---
type: experience
title: "Design Run — Atlas mesh-level indexing"
created: 2026-10-10
work_id: 2026-10-10-atlas-mesh-level-index
status: done
kva: alive
description: "Autogenesis design Run record. Found that the real mesh's 11 cross-store links are all short-form and none resolve, and that plain RRF over per-store lists is a rank interleave. Plan persisted and stopped for approval; agent-spec deferred."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-10-10-atlas-mesh-level-index.md
    kind: implements
  - path: autogenesis/plans/2026-10-10-atlas-mesh-level-index.md
    kind: derived_from
---

## What was asked

Run Autogenesis formal design (design operation only) for mesh-level indexing in the Atlas CLI, on top of atlas PR #61 (`feat/graph-query-drivers`, head `57198e4`, not merged): a mesh graph across mounted stores, federated recall fused with RRF, a CLI and config surface, and a harder multi-Atlas benchmark. Stop for approval. No implementation.

## What was done

- Entered root Autogenesis, operation design, with supports workflow-discipline, think-challenge and patterns. Change-class new-surface. work_id `2026-10-10-atlas-mesh-level-index`.
- Cloned the atlas repo at PR #61's head into a scratch directory. Mounted and resolved `github.com/sergio-sisternes-epam/atlas-atlas` (explicit id, as the mesh lists two stores), and mounted atlas-cartograph-atlas for the probe. Branched the store from the PR #27 branch (`244de59`).
- Read PR #61's index location, owner-token lock, driver overlay, graph, recall and mesh-file code, and the settled git-mesh decisions on `atlas://`, aliases and unresolved ids.
- Ran a scratch probe (scratch directory): merged both stores' projections (502 nodes, 2,195 edges, 5 ms), counted cross-store links (11, all short-form, 0 resolvable under the canonical grammar), timed fingerprints (2–32 ms per store), and fused real `--engine bm25` results with plain RRF k = 60 (rank interleave; any-word noise at ranks 2, 4 and 6 on one query).
- Search-grounded challenge: RRF on disjoint lists, cross-index BM25 statistics, index leakage of restricted content (CWE-612), budgeted agentic search. Pinned M1–M19.
- Persisted the plan, work hub and this record; compile green.

## Approval

Sergio approved the plan on 2026-10-10 at 23:08 BST (relayed to this Run), with the recommended answers to all three open questions:

1. Restricted pages are left out of mesh results by default, with no override in v1 (pin M20).
2. The resolver stays strict; the 11 short-form links get fixed with one small PR per store (pin M21).
3. Packets MA, MB, MC and MF are approved now; MD and ME follow after MB and MC are reviewed (pin M22).

Implementation runs through Copilot CLI once atlas PR #61 merges (pin M23). This Run recorded the approval only; it started no implementation. Plan and work hub status: `approved`.

## Deferred

- agent-spec `specify`: not in this harness's catalogue; deferred in the plan.
- In-process federated latency: only measured with one CLI subprocess per member; packet MF measures it.
- The multi-Atlas answer benchmark: runs only on Sergio's Mac (`~/scratch/atlas-answer-bench`).

## Contradictions recorded

- The atlas repo mesh row pins atlas-atlas at `docs/skill-help-pilot`; the Atlas card and earlier Runs use `main`. Mounting with `--ref main` left the gitlink commit `6c4ba92` (on `docs/skill-help-pilot`) checked out.
- Cross-store links in both stores use short forms (`atlas://atlas-cartograph-atlas/...`, `atlas://atlas-skill-memory/...`) that the settled canonical grammar does not resolve.

## Changed files

No product files. Atlas memory only:

```text
autogenesis/plans/2026-10-10-atlas-mesh-level-index.md (created)
work/2026-10-10-atlas-mesh-level-index.md (created)
autogenesis/experiences/2026-10-10-design-atlas-mesh-level-index.md (created)
autogenesis/plans/index.md (updated)
autogenesis/experiences/index.md (updated)
work/index.md (updated)
```
