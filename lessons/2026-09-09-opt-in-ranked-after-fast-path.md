---
type: lesson
title: "After fast path, opt into atlas:ranked; grep stays the basic default"
created: 2026-09-09
status: alive
kva: alive
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Leave grep until recall is enabled. The opt-in default atlas:ranked now beats grep on wall clock and follow-up read tokens. Skip atlas:tgrep. Use field filters when accuracy is the worry."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-fast-path-product-bench.md
    kind: derived_from
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: supersedes
  - path: lessons/2026-09-09-smr-fast-path-published-fts5.md
    kind: follows
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md
    kind: related
---

## Content

Measured on a 395-page atlas-atlas copy with a published FTS5 generation
(product CLI, `fast_path: true`). Skill surface: path `query` plus path
`configure`. Provenance:
[product bench](../experiences/2026-09-09-smr-fast-path-product-bench.md).

**Do**

1. Keep grep as the basic default (`recall.enabled=false`, SCHEMA 1.0 search).
2. When enabling recall, use `atlas:ranked` (activate default). Expect it to
   beat grep on wall clock (~80ms vs ~108ms here) and on the 1–3 pages the
   query path reads next (4–13× cheaper `read3`).
3. Prefer `type:` / `work_id:` / `path:` filters over an engine switch.
   Ranked is not always more accurate on bag-of-words queries.
4. Keep `atlas:tgrep` explicit and argv-only. Same rank as FTS5, slower, no
   token win until serve/subset-rank.

**Avoid**

- Citing the pre-fast-path ~7× SMR slowdown as current product behaviour.
- Enabling tgrep to chase speed, tokens, or grep noise.
- Upgrading a live 1.0 store only to search; bench on a copy.
