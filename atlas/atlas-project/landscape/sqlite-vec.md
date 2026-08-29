---
type: protostar
title: "Landscape — sqlite-vec / local index"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: open
kva: forming
growth: true
star_kind: probe
label: symbiont
description: "Embedded vector search in one SQLite file. Git-friendly only as a rebuildable derived artifact, not a mergeable SoR."
origin: third-party
sensitivity: public
sources:
  - https://github.com/asg017/sqlite-vec
  - https://github.com/unum-cloud/USearch
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-landscape-review.md
    kind: derived_from
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Growth path

Pair FTS5 (already the Atlas BM25 direction) with sqlite-vec in `.atlas/index.sqlite`. Rebuild on compile or checkout. Do not treat the binary index as mergeable across branches.

USearch is the compact on-disk ANN alternative if the corpus outgrows brute-force vec0.

## Open question

Commit the sqlite file per branch, or gitignore and rebuild? Merge conflicts on the db file are the failure mode.
