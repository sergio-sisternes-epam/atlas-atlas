---
type: experience
title: "Design Run — Atlas graph queries and nanograph versus BM25"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: done
kva: alive
description: "Autogenesis design Run record. Found --engine bm25 is a grep stub, nanograph has no Linux binary, and Atlas already holds the graph. Plan persisted and stopped for approval; live nanograph probe deferred."
origin: derived
sensitivity: internal
stage: design
relates_to:
  - path: work/2026-10-09-atlas-graph-query-nanograph.md
    kind: implements
  - path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
    kind: derived_from
---

## What was asked

Run Autogenesis formal design on Atlas: should nanograph replace or join the BM25 recall engine, and what graph capability should Atlas expose, treating the discuss skill's needs as first-class. Stop for approval. No implementation.

## What was done

- Entered root Autogenesis, operation design, with supports workflow-discipline, think-challenge and patterns. Change-class new-surface.
- Mounted and resolved `github.com/sergio-sisternes-epam/atlas-atlas` from a fresh clone of the atlas repo at `b0b1012` (v0.13.0). Branched the store from `origin/main`.
- Read the recall code. `--engine bm25` is a stub that always falls back to grep. Real BM25 is the `atlas:ranked` FTS5 profile. Graph neighbourhoods already exist in `core/retrieve.py`.
- Checked nanograph v1.3.0: MIT; macOS-only release binaries; no release since 2026-05-16; source build needs Rust 1.94.1 and protoc (box: 1.85.1, none).
- Ran the Atlas half of the fail-fast probe in scratch (`/workspace/nanograph-probe/`): exports to nanograph schema and seed, engine timings, a formula replica of nanograph BM25 (top-10 overlap with `atlas:ranked` 0.76 on atlas-atlas, 0.83 on waza-apm), and graph questions in milliseconds.
- Search-grounded challenge: KuzuDB abandonment, SQLite-is-enough at this scale, GraphRAG gains on multi-hop only.
- Persisted the plan and this record; compile green.

## Deferred

- Live nanograph probe: no Linux binary; source build needs Grand Maester tools.
- agent-spec `specify`: not in this harness's catalogue; deferred in the plan.

## Contradictions recorded

- The brief's standing decision says the store moved to the atlas repo's `atlas` branch. It has not; no such branch exists.
- The mesh row pins `docs/skill-help-pilot`; the Atlas card and earlier Runs use `main`.
- discuss lint L1 flags protostars that `implements` their work hub, which discuss's own sprout rule requires.

## Changed files

No product files. Atlas memory only:

```text
autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md (created)
work/2026-10-09-atlas-graph-query-nanograph.md (created)
autogenesis/experiences/2026-10-09-design-atlas-graph-query-nanograph.md (created)
autogenesis/plans/index.md (updated)
autogenesis/experiences/index.md (updated)
work/index.md (updated)
```
