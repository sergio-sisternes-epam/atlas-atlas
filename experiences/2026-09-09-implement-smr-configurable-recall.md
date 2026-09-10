---
type: experience
title: "Implement configurable Semantic Memory Recall (SMR)"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: closed
description: "Shipped SCHEMA 2.0 opt-in Coarse/Rank/Retrieve, scan and FTS5 drivers, gated tgrep, configure path, and upgrade CLI. Default 1.0 search is unchanged."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
---

## Context

Approved Autogenesis plan for configurable SMR. SMO stays skill-owned through
SCHEMA extensibility. tgrep stays a gated adapter. Existing stores must keep
grep search until explicit opt-in.

## What happened

Product code on Atlas 0.9.1 (Unreleased) adds JSON Draft 2020-12 contracts,
SCHEMA 1.0 to 2.0 upgrade with `atlas-compat-v1`, current-tree projection,
scan and fused SQLite FTS5 ranking, bounded directed graph retrieve, and
`atlas recall` plus `search --profile` / `--allow-partial`. Path `configure`
is the owner workflow. `atlas:tgrep` fails with
`unsupported_capability: disk_only_indexed_search` and never execs tgrep.

Repository tests: 13 entrypoints passed, including schema-governance
regression and new recall/upgrade/frontmatter suites.

## Outcome

Legacy init and search remain SCHEMA 1.0. Recall publishes an index only on
unfocused compile success when enabled. Installing a preset does not activate
it; uninstall of a selected namespaced preset fails closed.

Version stays 0.9.1 until a later release bump.

## Changed files

- `scripts/atlas_cli/schemas/*.schema.json`
- `scripts/atlas_cli/core/{jsonutil,recall_config,projection,recall_index,recall,retrieve,schema_upgrade,frontmatter,overlay}.py`
- `scripts/atlas_cli/core/drivers/{scan,fts5,tgrep}.py`
- `scripts/atlas_cli/commands/{recall,search,validate,init,schema_cmd}.py`
- `scripts/atlas_cli/cli.py`
- `references/paths/configure.md`
- `scripts/test_recall_*.py`, `scripts/test_schema_upgrade.py`, `scripts/test_frontmatter_v2.py`
- `SKILL.md`, `CHANGELOG.md`, `README.md`, `scripts/requirements*.txt`
