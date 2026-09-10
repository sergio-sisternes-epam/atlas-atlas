---
type: lesson
title: "Search KPIs: grep for speed on small stores; SMR for follow-up tokens"
created: 2026-09-09
status: superseded
kva: superseded
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Keep grep as default on small Atlases. Opt into SMR for follow-up read cost, not wall clock. tgrep is not a speed or token win until Rank skips a full current-tree FTS5 rebuild."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-kpi-bench.md
    kind: derived_from
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
  - path: lessons/2026-09-09-opt-in-ranked-after-fast-path.md
    kind: related
---

## Content

**Superseded** by [opt-in ranked after fast path](2026-09-09-opt-in-ranked-after-fast-path.md). The ~7× SMR slowdown was YAML projection, not FTS5.

Measured on atlas-atlas (~392 pages). Skill surface: path `query` plus path `configure`.

**Do**

1. Keep SCHEMA `query.search_engine: grep` as the default on small stores. It is ~7× faster than current-tree SMR here.
2. Treat token cost as **follow-up reads of 1–3 full pages**, not the hit JSON. Grep/scan term-count prefers long plans; that inflates `read3`.
3. Opt into SCHEMA 2.0 recall (`atlas:ranked` / published FTS5) when follow-up tokens matter and compile can publish a generation.
4. Use field filters (`type:`, `work_id:`) before switching engines. Exact filters were identical across engines.
5. Keep tgrep argv-only and digest-keyed. Do not start `serve` to chase latency.

**Avoid**

- Enabling `atlas:tgrep` to make a small Atlas faster. Coarse tgrep still pays ephemeral FTS5 Rank (~800–900ms) until a published index exists.
- Assuming FTS5/tgrep are always more accurate. Keyword-dense titles (`compile`) favoured grep/scan P@5 (0.80 vs 0.40).
- Counting grep JSON + 171 guidance tokens as the main leak. The protocol’s 1–3 page reads dominate.
- Upgrading a live 1.0 store just to bench SMR while 2.0 YAML still fail-closes on unquoted colon scalars.
