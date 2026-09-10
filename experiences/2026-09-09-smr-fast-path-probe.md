---
type: experience
title: "Probe: cheap fingerprint plus published FTS5 beats grep; tgrep does not"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: closed
description: "On a 390-page published generation, stat fingerprint is 15ms and FTS5 MATCH ~1ms. digest+FTS5 ~17ms vs grep ~140–180ms. tgrep coarse matched ~⅓ of the store and did not change top hits."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-kpi-bench.md
    kind: follows
  - path: lessons/2026-09-09-smr-fast-path-published-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
---

## Context

After quoting three SCHEMA 2.0 YAML failures, compile published FTS5. Product SMR still paid `project_store` (~736ms). We probed a non-product pipeline: cheap path+size+mtime digest, tgrep coarse, Rank only on those paths, vs digest+full FTS5 vs grep.

## What happened

| Mode | SMR query | compile | overlay |
|---|---:|---:|---:|
| grep | 179ms / 16k read3 | 141 / 9.3k | 144 / 20k |
| cheap digest | 15ms (390 files) | same | same |
| `project_store` | 736ms | same | same |
| digest+FTS5 full | **17ms** / 3.4k | **17** / 0.96k | **16** / 2.8k |
| digest+tgrep+subset | 55ms / 3.4k | 78 / 0.96k | 57 / 2.8k |
| tgrep coarse only | 23ms, 123 hits | 26ms, 187 | 24ms, 130 |

tgrep top-3 matched full FTS5. Token-OR coarse does not shrink Rank on this corpus.

## Lesson

Skip YAML projection when a published generation matches a cheap fingerprint. Park tgrep as an advanced profile until coarse actually reduces Rank or `serve` is an explicit later pin.
