---
type: experience
title: "KPI bench: grep vs scan vs FTS5 vs tgrep on atlas-atlas"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: closed
description: "On a 392-page copy, grep is ~7x faster; token cost is follow-up page reads, not hit JSON. FTS5/tgrep can cut read-3 tokens when they rank shorter pages."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: related
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
---

## Context

User asked to analyse grep vs SMR on speed, tokens, and accuracy. Concern: grep is fast on small atlases but token-intensive.

Live atlas-atlas stayed SCHEMA 1.0. SMR profiles ran on an upgraded copy with `--allow-partial` (three 2.0 YAML parse omissions). tgrep 1.0.5 on PATH. Limit 20. Token proxy = chars/4. `read3` = size of the top three hit files (query protocol: read 1–3 pages).

## What happened

| Query | Engine | ms | JSON tok | Guidance | read3 tok | P@5 | MRR |
|---|---|---:|---:|---:|---:|---:|---:|
| semantic memory recall | grep | 117 | 5530 | 171 | 15759 | 1.00 | 1.00 |
| | scan | 825 | 5377 | 0 | 15759 | 1.00 | 1.00 |
| | FTS5 | 859 | 2795 | 0 | 3280 | 1.00 | 1.00 |
| | tgrep+FTS5 | 911 | 4407 | 0 | 3280 | 1.00 | 1.00 |
| compile | grep | 129 | 6106 | 171 | 9328 | 0.80 | 1.00 |
| | FTS5 / tgrep | ~840–950 | 4.6–5.5k | 0 | 959 | 0.40 | 0.50 |
| schema overlay | grep | 120 | 6041 | 171 | 19611 | 0.80 | 1.00 |
| | FTS5 | 854 | 1252 | 0 | 15314 | 0.67 | 0.50 |

Scan hit-set matched grep (same term-count scorer). tgrep coarse without case-insensitive tokens returned empty multi-word sets; that was fixed before this table. Rank for `atlas:tgrep` is still ephemeral FTS5, so tgrep did not beat FTS5 on speed or tokens.

## Lesson

Grep JSON is not the token leak. Follow-up full-page reads are. Keep grep as the small-store default. Use SMR when ranking can shrink those reads. See the lesson page.
