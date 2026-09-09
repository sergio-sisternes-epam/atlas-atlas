---
type: protostar
title: "Improve tgrep: serve, subset Rank, tighter coarse"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "tgrep is kept as the advanced profile with limited benefits. Later: optional serve, Rank only tgrep paths, and coarse tighter than token-OR. New pin required before serve."
relates_to:
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: derived_from
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-fast-path-probe.md
    kind: derived_from
  - path: lessons/2026-09-09-smr-fast-path-published-fts5.md
    kind: related
---

## Skill pointer

Atlas path `configure` and profile `atlas:tgrep`. Do not enable `tgrep serve` until this leaf is designed and pinned.

## Why it is weak today

Coarse token-OR returns ~⅓ of a small Atlas. Rank still runs full-corpus FTS5. argv reloads the index per query. microsoft/tgrep headlines assume `tgrep serve` on 15k–500k files.

## Recommendations (not authority)

1. **Subset Rank.** FTS5 `MATCH` restricted to tgrep paths (or Python BM25 on those rows only). Coarse must shrink Rank.
2. **Optional serve.** Long-lived `tgrep serve` plus argv client, Atlas-owned, no `--no-index`. Requires a new settled pin that relaxes never-serve.
3. **Tighter coarse.** Phrases / AND of tokens, not `|` of every token; post-filter to projection without dumping every JSON match line.
4. **Skip projection** the same cheap-fingerprint gate as `atlas:ranked`, using sqlite paths as the admitted set.
5. **Do not** activate tgrep to chase latency on stores of a few hundred pages; use `atlas:ranked`.
