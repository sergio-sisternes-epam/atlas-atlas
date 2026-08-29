---
type: document
title: "Atlas glossary"
created: 2026-08-27
promoted: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: alive
kva: alive
description: "Normative labels for landscape write-back and comparison memory. Lives next to the Atlas root index."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/landscape-review/current-branch.md
    kind: derived_from
  - path: experiences/2026-08-27-vision-and-comparison-discussion.md
    kind: derived_from
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
  - path: atlas-project/comparison-correct.md
    kind: related
  - path: atlas-project/vision.md
    kind: related
---

## Content

Normative for path `landscape`. Partner and competitor pages use these labels.

| Term | Meaning |
|---|---|
| rival | Same job as Atlas, different source of truth |
| neighbour | Same architectural bet; missing compile, work hubs, or mesh/PR |
| projector | Enterprise read-path or map of compile-green Atlas pages |
| symbiont | Complements Atlas; we interoperate; Atlas stays SoR |
| out-of-frame | Not in the living comparison set unless it grew a git SoR |
| realization | Projector that implements the Atlas blueprint at estate grade (Microsoft first) |
| SoR | Source of record — compile-green git pages, not the search index |
| work hub | `type: work` page clustering a `work_id` |
| mount | Atlas store attached (submodule/worktree) so another team can read and PR |
| compile-green | `atlas compile --root` exit 0 |
| KVA terminate | Never-fit frame; keep the page; alive exit-reason node |
| KVA supersede | Was fit; successor exists |
| reshape | Edit an alive page; not an exit ramp |

A name may be projector and symbiont. It must not be rival and projector for the same job.

## Search aliases

Bounded extra tokens for Atlas path `query` (second search only). Do not treat this table as free-form expansion.

| Query token | Add (at most these) |
|---|---|
| bm25 | FTS5, `.atlas-index`, search_engine, answerability, sqlite-vec |
| cli surface | validate, compile, search, migrate, promote, init |
| query path | rewrite, glossary, spine, type: |
| harness | hit cards, work_id, kva |
| navigation signals | kva, work_id, relates_to, type: |
