---
type: document
title: "Orbit — may write paths use focused compile?"
created: 2026-08-27
work_id: 2026-08-27-compile-project-skill
status: settled
kva: alive
reality: current
description: "Settled L1: write paths unfocused only. Lenses belong to path compile. Operator 2026-08-27."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-project-skill/enter-scope.md
    kind: follows
  - path: work/2026-08-27-compile-project-skill.md
    kind: implements
  - path: autogenesis/discuss/compile-project-skill/hub.md
    kind: related
---

## Content

E2: other paths call `atlas compile` as a tool and must follow the compile-path contract. This orbit is which flags they may pass.

Store-level checks still run under a lens. A green `--path` compile is not session-close. That is already claimed on the origin protostar.

### Options

**L1 — Write paths: unfocused only.**  
`atlas compile --root <atlas>`. Lenses belong only to `path: compile`. Simple. Pays a full page walk on every remember/discuss persist.

**L2 — Write paths may lens the pages they just wrote.**  
`--path` (and `--type` when the slice is one type) during the edit loop. Session close, or any path that claims the *store* is healthy, must still run unfocused compile. Matches the origin star.

**L3 — Write paths may `--path` only; `--type` is `path: compile` only.**  
Narrower tool surface. `--type` is a repair lens, not a “I touched three experiences” lens.

### Tension

This session already used focused compile while editing discuss pages, then unfocused at close — that is L2 in practice. L1 would forbid that habit. L3 stops an agent from hiding other-type contract misses mid-remember.

### Probe (this Atlas, 2026-08-27)

This skill Atlas: 196 markdown files. Wall clock (one run):

- unfocused compile: **0.34s**, exit 0
- `--path autogenesis/discuss/compile-project-skill/`: **0.17s**, 5 pages
- `--type work`: **0.14s**

Cost is not the hinge here. A project Atlas can be much larger; this path is for those stores too.

What a lens still does (0.7.6 pin): SCHEMA, staging, mesh, and index rules run on the **whole** store. Only the **page-contract walk** is filtered. Focused green can still catch empty-staging and broken SCHEMA. It will **not** list page-contract warnings outside the lens (missing `implements`, protostar without `derived_from`, forming-document).

Remember today hard-codes unfocused compile (L1 in prose). This discussion already used L2 in practice.

### Failure modes

- Treat focused green as store-healthy → dirty pages outside the lens stay silent until unfocused compile. E2 already forbids calling that session-close; agents still skip.
- L1 on a large project store → agents skip compile because the walk is slow. Worse than a mid-loop lens.
- Mid-remember `--type experience` → hides every other type’s contract miss. `--path folder/` still walks mixed types in that folder.
- Mid-remember `--path file.md` only → work-cluster neighbours are not walked unless they sit under that prefix (parked related-files rule).

### How to use Q2

If session-close is **always** unfocused, L2/L3 are mid-loop shortcuts. If close may stay focused when “I only touched this folder”, that is green-lens-as-close. The origin protostar already said no.

### Not this orbit

The exact related-files rule (same folder vs `relates_to` vs work-cluster). Implement.

## Answer (operator 2026-08-27)

**L1.** Write paths run unfocused `atlas compile --root <atlas>` only. `--path` / `--type` belong to `path: compile`. L2 and L3 are alternative, not current. Q2 on this page is unused (no write-path lens).

## Batch

1. Settled L1.
2. Unused. Close-out for `path: compile` moves with related-files.
