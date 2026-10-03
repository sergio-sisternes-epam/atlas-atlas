---
type: experience
title: "Implement Atlas recall rename (path query and search)"
created: 2026-10-04
work_id: 2026-10-04-atlas-recall-rename
implements: 2026-10-04-atlas-recall-rename
closes: 2026-10-04-atlas-recall-rename
plan_path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
status: closed
origin: internal
sensitivity: internal
description: "Approved plan t226u implemented on pull request 42. Path recall, atlas recall run, recall_cmd. Hard cut in this 0.13 beta. SCHEMA key query stays."
relates_to:
  - path: autogenesis/work/2026-10-04-atlas-recall-rename.md
    kind: implements
  - path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
    kind: related
  - path: decisions/2026-10-04-recall-renames-query-path-and-search.md
    kind: related
  - path: work/2026-10-03-atlas-memory-layers.md
    kind: related
---

## Context

Sergio approved before the plan was shown (approval_ref t226u). Parent bound disposition approved and started implement. Product edits are on branch `implement/2026-10-03-atlas-memory-layers`, implement commit `08cc045f8f767f47e5dbf08aa22b98fbcdd76151`, pull request https://github.com/sergio-sisternes-epam/atlas/pull/42. Version remains 0.13.0-beta scope (package 0.13.0). Not merged and not tagged.

Pins held: path `query` → `recall`; root commands `search` and `query` removed (hard cut); discovery is `atlas recall run` on the existing recall group; receipt `recall_cmd` / `stopped_at: recall_hit`; SCHEMA key `query` unchanged; walk unchanged; memory-layers pins not reversed.

agent-spec is not installed. Behavioural contract stays deferred. No `.feature` files were written. Scenario `references/scenarios/recall-rename-adversarial-v1.yaml` materialised; `memory-layers-adversarial-v1.yaml` kept.

Later follow-ups on the same PR branch (not part of this plan's changed files): schema exact-array const regressions (`e988cd9`), and compile JSON `memory_rung` plus SKILL `--dry-run` docs (`4d5e90b`).

## Evaluation

Commands run in `/workspace/atlas-memory-layers` after the implement commit. Exit codes are the process status.

- `test -f references/paths/recall.md` and `test ! -f references/paths/query.md` — pass. File contains `recall_cmd`, not `search_cmd`.
- Click registry: root has `recall`, no `search` or `query`; `recall` has `run`, `status`, `index`/`build`.
- `python3 scripts/test_memory_layers.py` exit 0 (recall.md assertions; absent `memory.rung` remains info exit 0).
- `python3 scripts/test_recall_config.py` exit 0.
- `python3 scripts/test_recall_pipeline.py` exit 0 (`recall run` invocations).
- `python3 scripts/test_activation_cards.py` exit 0.
- `python3 scripts/test_help_paths.py` exit 0.
- `python3 scripts/test_ci_activation.py` exit 0.
- `python3 scripts/run_tests.py` exit 0. All 16 repository test entrypoints passed.
- Live smoke: `atlas recall run` returns hits; `atlas search` / `atlas query` are ordinary Click "No such command" errors. SCHEMA init still has key `query`.

## Changed files

- `.agents/skills/panel-review/references/lenses/atlas-contract.md`
- `.apm/skills/panel-review/references/lenses/atlas-contract.md`
- `CHANGELOG.md`
- `README.md`
- `SKILL.md`
- `references/help/index.md`
- `references/paths/configure.md`
- `references/paths/getting-started.md`
- `references/paths/help.md`
- `references/paths/query.md` → `references/paths/recall.md`
- `references/paths/remember.md`
- `references/paths/work.md`
- `references/scenarios/recall-rename-adversarial-v1.yaml`
- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/search.py`
- `scripts/test_activation_cards.py`
- `scripts/test_ci_activation.py`
- `scripts/test_help_paths.py`
- `scripts/test_memory_layers.py`
- `scripts/test_recall_pipeline.py`
- `scripts/test_schema_upgrade.py`

## Outcome

The skill pull request remains open. Hard cut landed in this beta. Store SCHEMA key `query` was not migrated.
