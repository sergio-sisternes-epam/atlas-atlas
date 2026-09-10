---
type: lesson
title: "SMR speed win is published FTS5 plus cheap freshness, not tgrep"
created: 2026-09-09
status: alive
kva: alive
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Keep grep until opt-in. The next configuration is atlas:ranked with a published generation and a cheap fingerprint so query skips YAML projection. tgrep stays advanced and does not beat FTS5 on small stores."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-fast-path-probe.md
    kind: derived_from
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: follows
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md
    kind: related
  - path: autogenesis/plans/leaves/p-tgrep-serve-and-subset-rank.md
    kind: related
---

## Content

**Do**

1. Leave grep as the SCHEMA default (`recall.enabled=false`).
2. When enabling recall, select `atlas:ranked` (published FTS5). Query may skip `project_store` when the cheap fingerprint matches `current.json`.
3. Treat follow-up page reads as the token KPI; ranked hits already cut those vs term-count grep.
4. Keep `atlas:tgrep` explicit and argv-only. Do not expect speed or token wins on hundreds of pages.

**Avoid**

- Measuring SMR latency while still YAML-projecting every query, then concluding FTS5 is slow.
- Enabling tgrep to fix grep noise; Rank is FTS5, coarse was not shrinking it.
- Using mtime as the only stored truth. Publish still records content `corpus_digest`. Cheap fingerprint is the query gate.
- Turning on `tgrep serve` without a new pin (see the tgrep protostar).
