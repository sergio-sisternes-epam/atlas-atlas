---
type: lesson
title: "Search harness and hubs before BM25 (hypothesis)"
created: 2026-08-27
status: forming
work_id: atlas-bm25-and-live-migration-v1
description: "Two-probe revision: grep is easy on store vocabulary against one page; hard on synonyms and on synthesis questions with no spine page. Harness + hubs first. FTS5 BM25 next. Vectors later."
origin: derived
sensitivity: internal
relates_to:
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: implements
  - path: experiences/2026-08-27-search-self-atlas-bm25-hard-query.md
    kind: derived_from
  - path: experiences/2026-08-27-search-self-atlas-cli-evolution-probe.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase3.md
    kind: related
  - path: atlas-project/landscape/sqlite-vec.md
    kind: related
  - path: autogenesis/discuss/git-mesh/scope-storage-not-query.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/find-by-type.md
    kind: related
---

## Content

**Hypothesis (revised after two probes):** grep-mode Atlas search has three difficulty classes, not two.

| Class | Example | Result |
|-------|---------|--------|
| Token + one page | `how atlas search works` → Phase 3 experience | Easy. One search, one read. |
| Synonym / all-ideas | `bm25` when ideas live under FTS5 | Hard. Rewrite + hops. Thin hub. |
| Synthesis / why / evolve | `how did the CLI evolve` | Medium. Pieces titled well; no spine page. Natural language ranks the wrong plans. Store phrase `cli surface` + `type:experience` finds the pieces. |

Titles on *parts* do not make a *timeline* query easy. The missing object is a page whose title matches the question class (evolution, all-ideas), not a better engine.

**Do**

1. Use `atlas search` as a candidate list. Read 1–3 pages. Expand `relates_to`. Never treat `staging/` as an answer.
2. On hard queries, rewrite before the second scan: add glossary aliases and index words (`bm25` → `FTS5`, `.atlas-index`, `search_engine`).
3. Filter on frontmatter first (`type:`, later `work_id:`, `kva:`). Ranking is not inventory. Type listing is not blocked on BM25.
4. Compile living ideas onto the work hub so “all ideas on X” has one high-title hit.
5. When an index exists, use SQLite FTS5 BM25 with title ≫ description ≫ body. Rebuild on compile. Do not merge the binary index across branches.
6. Keep query ranking out of the git-mesh discussion. Azure / vector search stays a derived projector, not authorship.

**Avoid**

- Unbounded whole-tree grep as the primary discovery method.
- Treating “mentions BM25 to exclude it” as “about BM25.”
- Adding embeddings before measuring grep + metadata filters + a filled hub.
- Waiting for live okf-wiki migration to make search usable.

**Predicted contrast (original):** a later query that names a pinned decision or a unique title should be one search and one or two reads.

**Probe result:** partially confirmed. Cost dropped (≈10 reads → ≈6). Natural-language evolution query still needed a rewrite to store vocabulary. Failure mode is “no page for this question class,” same as the BM25 stub hub.

**Before Autogenesis design**

- Do not start a search-engine workstream. Start with query-path rewrite, hit cards (`type`, `work_id`, `kva`, match field), glossary aliases, and compiling spine pages (CLI evolution; BM25 idea list).
- Honour the already-written verb split: `compile` = gate, `search` = ranked discovery, inventory ≠ compile flags (`cli-compile-list-review.md`). 0.7.5 bolted `--list-type` onto compile and 0.7.6 had to rip it out.
- Keep query ranking out of git-mesh. Type filter stays orthogonal to BM25.
- FTS5 title-weighted BM25 remains next index step, not the first design packet.
