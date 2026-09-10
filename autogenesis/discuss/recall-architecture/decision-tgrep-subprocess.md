---
type: decision
title: "tgrep runs as argv subprocess against a digest-keyed on-disk index"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Accepted: Atlas may invoke a local tgrep binary as argv subprocess to build and query an Atlas-owned on-disk index rebuilt on projection digest mismatch; never serve, never auto-install, never silent grep fallback."
status: settled
kva: alive
origin: user
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: records
  - path: autogenesis/discuss/recall-architecture/decision-json-configuration.md
    kind: related
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
---

## Decision

Relax the earlier "never subprocess" tgrep gate. Atlas may call a `tgrep`
binary already on `PATH` using a fixed argv list (no shell).

The index lives at `.atlas-index/tgrep/` inside the store, not the upstream
`.tgrep/` directory. Rebuild when the current-tree projection digest
mismatches. Search that index. Never run `tgrep serve`, never write
`serve.json`, never pass `--no-index`.

A missing binary fails closed as `unsupported_capability: tgrep_binary_missing`.
A detected `serve.json` fails closed as `tgrep_serve_detected`. Hits are
post-filtered to admitted projection pages.

tgrep is Coarse only. Rank and Retrieve stay Atlas drivers. Do not auto-install
tgrep. Do not claim daemon-class acceleration.

## Rationale

Upstream now documents on-disk search without `serve` (`tgrep index`, then
`tgrep` against `--index-path`). Atlas still requires current-tree correctness,
so a digest-keyed rebuild is the freshness contract. An in-process library
binding is not available as a supported Atlas dependency.

## Alternatives considered

- Keep the gate and use FTS5 as the only accelerated path.
- Bind `tgrep-core` in-process with no CLI.
- Allow `tgrep serve` for hot search.

Rejected: the user selected argv subprocess plus digest rebuild, never serve.

## Consequences

- `atlas:tgrep` may be selected on SCHEMA 2.0 stores.
- CI without `tgrep` must fail honestly, not skip to grep.
- A user-started tgrep daemon in the store is unsupported and blocked.
- Ephemeral index rebuilds on small corpora will not beat FTS5.
