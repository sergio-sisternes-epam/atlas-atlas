---
type: experience
title: "Implement Run: real BM25 engine, atlas graph and driver overlay"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: done
kva: alive
description: "Packets A, B and C of the approved plan (revision 1) were implemented by fresh Copilot CLI sessions on atlas branch feat/graph-query-drivers (PR #61, head 16c3b44). The nanograph driver is enabled only on macOS arm64 and has not yet been checked against a real nanograph binary."
origin: derived
sensitivity: internal
stage: implement
implements: work/2026-10-09-atlas-graph-query-nanograph.md
plan_path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
relates_to:
  - path: work/2026-10-09-atlas-graph-query-nanograph.md
    kind: implements
  - path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
    kind: derived_from
  - path: autogenesis/experiences/2026-10-09-design-atlas-graph-query-nanograph.md
    kind: follows
---

## What was asked

On 2026-10-09 at 13:54 BST, Sergio approved packets A, B and C. Built-in drivers stay the default everywhere, and nanograph is enabled only on macOS arm64. A driver overlay leaves room for future Windows and Linux drivers. Only Copilot CLI writes product code, with a fresh session for each packet and no version bump.

## What was done

- **Branch:** `feat/graph-query-drivers` in `sergio-sisternes-epam/atlas`, from `b0b1012` (v0.13.0). PR [#61](https://github.com/sergio-sisternes-epam/atlas/pull/61), head `16c3b442543d093654e54732f810406e05a73da1`. It is not merged and no Copilot review was requested.
- **Packet A, `58c6075`:** `--engine bm25` runs on SQLite FTS5 (fast path or a temporary index), with a labelled any-word retry and the `.atlas-index/` ignore guard.
- **Packet B, `d90ae24`:** `atlas graph nodes|edges|neighbours|export`, built on the shared projection, with golden nanograph export fixtures.
- **Packet C, `16c3b44`:** the driver interface, registry and platform matrix, plus the nanograph driver. It is gated to darwin/arm64 with version 1.3.0 or later, called with argument lists and timeouts, and run with embedding keys stripped. Its index lives under `.atlas-index/nanograph/<generation>/`. Commands added: `atlas graph drivers`, `--engine nanograph` and `--driver nanograph`.
- **Tests and checks** on Linux x86_64, with no nanograph present:
  - `run_tests.py` passed all 23 entrypoints.
  - `release_readiness.py --commit 16c3b44` passed.
  - `apm audit` found no issues.
  - The diff scan found no private host name and no tokens.

## Changed files

- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/search.py`, `recall.py`, `validate.py`, `graph.py` (new)
- `scripts/atlas_cli/core/graph.py` (new), `driver_overlay.py` (new), `ignore_guard.py` (new), `projection.py`, `recall.py`, `retrieve.py`
- `scripts/atlas_cli/core/drivers/fts5.py`, `nanograph.py` (new)
- `scripts/test_recall_bm25.py`, `test_graph.py`, `test_drivers.py`, `test_nanograph_live.py` (all new)
- `fixtures/graph/schema.pg`, `fixtures/graph/seed.jsonl` (new)
- `SKILL.md`, `references/graph.md` (new), `references/drivers.md` (new), `references/paths/recall.md`, `CHANGELOG.md` (`## Unreleased (targets 0.14.0)`)

## Deviations from the plan

- The nanograph index is reused only when both the corpus digest and the nanograph version match. The plan asked only for the digest; this is stricter.
- nanograph `neighbours` makes one subprocess call per page, edge kind and direction at each hop. That is correct but could be slow on large neighbourhoods.
- `--engine bm25` output now also carries `driver_used`.
- The recall neighbourhood now resolves `relates_to` targets written with a leading `./`, because it uses the shared helper. This is a small behaviour change.
- `--engine nanograph`, like every `--engine` value, still conflicts with enabled recall. That keeps the existing rule. The driver can be reached through recall only on stores where recall is off.

## Still not proven

- The `.gq` syntax, the seed format and the field names in `nanograph run --format json` output have not been run against a real nanograph binary. The PR body has the manual check commands for an Apple Silicon Mac. `scripts/test_nanograph_live.py` covers them there and skips everywhere else.

## Consequences flagged, not acted on

- Releasing 0.14.0 belongs to Master of Packages.
- nanograph is an optional binary that users install themselves on macOS. It adds no box-restore or Grand Maester dependency.
