---
type: experience
title: "Product KPI bench: ranked fast path beats grep on speed and read3"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: closed
description: "On a 395-page SCHEMA 2.0 copy with a published generation, atlas:ranked (fast_path true) is ~80ms vs grep ~108ms and 4-13x cheaper on follow-up page reads. tgrep matches ranked hits but is slower."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-kpi-bench.md
    kind: follows
  - path: experiences/2026-09-09-smr-fast-path-probe.md
    kind: follows
  - path: lessons/2026-09-09-opt-in-ranked-after-fast-path.md
    kind: related
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
---

## Context

After the cheap-fingerprint fast path landed in product search, we re-ran
speed / tokens / accuracy on a copy of atlas-atlas (live store stayed SCHEMA
1.0). Upgrade + compile published a complete generation (395 pages). Limit 20.
Token proxy = chars/4. `read3` = size of the top three hit files. Median of
three timed CLI runs after one warmup.

## What happened

| Query | Engine | ms | JSON tok | read3 tok | P@5 | MRR | fast_path |
|---|---|---:|---:|---:|---:|---:|---|
| semantic memory recall | grep | 109 | 4121 | 16216 | 1.00 | 1.00 | n/a |
| | ranked | 80 | 2247 | 3736 | 0.60 | 1.00 | true |
| | tgrep | 130 | 3159 | 3736 | 0.60 | 1.00 | true |
| compile | grep | 110 | 4594 | 9328 | 0.20 | 0.33 | n/a |
| | ranked | 82 | 4207 | 959 | 0.40 | 1.00 | true |
| | tgrep | 148 | 3294 | 959 | 0.40 | 1.00 | true |
| schema overlay | grep | 106 | 4556 | 19611 | 0.20 | 0.25 | n/a |
| | ranked | 81 | 1226 | 1517 | 0.00 | 0.00 | true |
| | tgrep | 131 | 3917 | 1517 | 0.00 | 0.12 | true |

The earlier ~7× SMR slowdown was YAML `project_store` on every query. Product
ranked now skips that when the cheap fingerprint matches. tgrep used the same
FTS5 rank (identical top hits to ranked) and paid extra coarse time.

Accuracy is mixed: grep still wins bag-of-words on noisy queries; ranked
prefers shorter topical pages and cuts follow-up reads.

## Lesson

Opt into `atlas:ranked` after compile can publish. Keep grep until that
opt-in. Do not enable `atlas:tgrep` for speed or tokens. See
[opt-in ranked lesson](../lessons/2026-09-09-opt-in-ranked-after-fast-path.md).
