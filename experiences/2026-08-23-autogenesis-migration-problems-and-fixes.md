---
type: experience
title: "Autogenesis wiki→Atlas migration: problems encountered and how they were fixed"
created: 2026-08-23
work_id: atlas-migrate-cli-improve-v1
status: done
description: "Retrospective of the live full-directory migrate of autogenesis references/wiki into references/atlas. Documents CLI/skill friction and the recovery path that left staging at 0 with dense relates_to."
relates_to:
  - path: work/atlas-migrate-cli-improve-v1.md
    kind: implements
  - path: work/autogenesis-okf-wiki-to-atlas-migration-v1.md
    kind: records
  - path: decisions/prefer-atlas-over-okf-wiki-interim.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase4.md
    kind: related
---

## Context

User directed: migrate autogenesis process memory from okf-wiki to Atlas using the **atlas migrate CLI**, then switch Autogenesis discipline to Atlas-only. Several incorrect intermediate approaches were corrected until a thorough pass left staging empty and compile green.

## What happened — problems

### P1 — Selective single-file migrate treated as “done”
Early pass called `atlas migrate` only on three knowledge files, rewrote scaffolds by hand, and claimed content migrated. User rejected: the CLI supports full **directory** migrate; selective-only under-used the tool.

### P2 — Promote does not carry original body
`atlas promote` scaffolds from a **template** only. Original staging body is not copied into the target. Agents must re-read source (or staging before clear) to complete claims. Easy to forget and leave thin pages (compile fails `not_just_links`).

### P3 — Full-directory migrate fills staging (179 files); compile hard-fails
Correct `atlas migrate <wiki-dir> --root <atlas>` placed the entire tree under `staging/`. Compile refuses non-empty staging (`no_answerable_in_staging`). No CLI helper for inventory summary, batch promote, or “clear with deferral”.

### P4 — Target already exists blocks promote
Re-promote of pages already written as decisions failed with “target already exists”. No `--force` / skip-existing mode.

### P5 — Bulk claim conversion is agent work, not CLI
Converting 31 knowledge + 139 experiences into claim-bearing pages with valid frontmatter, required sections, and dense `relates_to` required a custom agent script. CLI has no batch promote or mesh assist.

### P6 — Broken relates_to from keyword heuristics
Thematic auto-linking injected non-path tokens into frontmatter (`evolve`, `Exit`, `review-package` as bare words). Compile later flagged missing frontmatter when a bad cleaner ran. Fixed by restoring three experiences from the old wiki and rewriting clean edges.

### P7 — Discipline vs content order
Discipline (SKILL.md / workflow-discipline) was switched before content migration was complete. User focus stayed on CLI correctness first; discipline switch remained valid once content landed.

## What happened — fixes

| Problem | Fix applied |
|---------|-------------|
| P1 | Re-ran **full-directory** `atlas migrate` on `references/wiki` |
| P2 | Agent completed every promoted page with claim-bearing body (Decision/Rationale/Consequences or Context/What happened/Outcome) |
| P3 | After claim conversion, **cleared staging completely**; compile green |
| P4 | Skipped already-mapped stems; wrote remaining knowledge as new decision paths |
| P5 | Python conversion pass: all knowledge → decisions, all raw experiences → experiences, 10 historical work hubs for edge resolution |
| P6 | Frontmatter-only relates_to validation; restored 3 broken pages; 0 broken edges (688 total) |
| P7 | Discipline Atlas-only kept; backed by migrated decision surface |

## Outcome

Autogenesis Atlas root final state:
- decisions: 32  
- experiences: 144  
- work hubs: 11  
- staging: **0**  
- `atlas compile` exit 0  
- 688 relates_to edges, 0 broken  

Migration work `autogenesis-okf-wiki-to-atlas-migration-v1` closed. Improvement ideas captured under **draft** work `atlas-migrate-cli-improve-v1`.

## Follow-ups

- Design + implement CLI/skill improvements (this work hub).
- Keep bulk BM25 / live migration under `atlas-bm25-and-live-migration-v1`.
