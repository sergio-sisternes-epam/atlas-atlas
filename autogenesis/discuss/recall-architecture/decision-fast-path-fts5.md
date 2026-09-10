---
type: decision
title: "Query FTS5 without YAML projection when cheap fingerprint matches"
created: 2026-09-09
status: settled
kva: alive
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Publish stores corpus_digest plus a path/size/mtime fingerprint. Matching queries open the published sqlite and skip project_store. Mismatch auto-rebuilds then searches."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: experiences/2026-09-09-smr-fast-path-probe.md
    kind: derived_from
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: related
---

## Decision

Current-tree **answers** stay mandatory. Current-tree **YAML parse on every query** does not.

At publish, write `corpus_digest` (content) and `cheap_fingerprint` (eligible path + size + mtime_ns). At query, recompute the cheap fingerprint. Match and `complete: true` → open published FTS5, no `project_store`. Mismatch → project, publish if recall is enabled, then search.

mtime can false-match if content changes without a timestamp change. That risk is accepted for this cut; content sha remains the published generation id.

## Why

Probe: cheap digest 15ms, FTS5 MATCH ~1ms, YAML projection 736ms. Digest+FTS5 already beat grep (~17ms vs ~150ms) with the same token cut.
