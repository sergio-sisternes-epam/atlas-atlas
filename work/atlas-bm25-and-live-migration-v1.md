---
type: work
title: "Atlas BM25 search and live okf-wiki migration"
created: 2026-08-23
work_id: atlas-bm25-and-live-migration-v1
status: draft
description: "Deferred product work: real BM25 index + engine, and live migration of okf-wiki content into Atlas."
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: follows
  - path: experiences/2026-08-27-search-self-atlas-bm25-hard-query.md
    kind: related
  - path: experiences/2026-08-27-search-self-atlas-cli-evolution-probe.md
    kind: related
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: atlas-project/landscape/sqlite-vec.md
    kind: related
---

## Scope

BM25 index/query and live okf-wiki migration with answerability checks.

## Status

**Draft** — not started.

## Outcomes (target)

See design notes on deferred construct smokes relative-index-portable and answerability-concrete.

## Ideas already in this store (spine)

Not started. Living claims live on the linked pages.

- Grep pilot shipped; `--engine bm25` falls back without `.atlas-index/` — `experiences/2026-08-23-implement-atlas-phase3.md`
- Local direction: SQLite FTS5 (+ optional sqlite-vec) in a rebuildable index file, not a mergeable SoR — `atlas-project/landscape/sqlite-vec.md`
- md-graph as FTS5 symbiont, not a second SoR — `atlas-project/landscape/md-graph.md`
- Type inventory is not BM25 — `autogenesis/discuss/compile-type-contract/find-by-type.md`
- Query ranking stays out of git-mesh — `autogenesis/discuss/git-mesh/scope-storage-not-query.md`
- Azure AI Search is a derived BM25+vector projector — `atlas-project/partners/azure-ai-search.md`, `atlas-project/azure-planes.md`
- Harness-before-index hypothesis (two probes) — `lessons/2026-08-27-search-harness-before-bm25.md`
- FTS5 implement parked — `autogenesis/plans/leaves/p-fts5-bm25-index.md`
