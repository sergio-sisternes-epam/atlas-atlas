---
type: experience
title: "Implement Atlas memory layers (0.13.0)"
created: 2026-10-03
work_id: 2026-10-03-atlas-memory-layers
implements: 2026-10-03-atlas-memory-layers
closes: 2026-10-03-atlas-memory-layers
plan_path: autogenesis/plans/2026-10-03-atlas-memory-layers.md
status: closed
origin: internal
sensitivity: internal
description: "Approved plan t205u implemented as Atlas 0.13.0 on pull request 42. Compile info rung does not fail existing stores."
relates_to:
  - path: work/2026-10-03-atlas-memory-layers.md
    kind: implements
  - path: autogenesis/plans/2026-10-03-atlas-memory-layers.md
    kind: related
---

## Context

Sergio approved plan `autogenesis/plans/2026-10-03-atlas-memory-layers.md` in chat t205u ("Approved. Proceed"). Product edits are on branch `implement/2026-10-03-atlas-memory-layers`, commit `e16aa31edaa537215fcf2cc0510e19d08125858e`, pull request https://github.com/sergio-sisternes-epam/atlas/pull/42. Version 0.13.0. Not merged and not tagged.

agent-spec is not installed. Behavioural contract stays deferred. No `.feature` files were written.

## Evaluation

Commands run in the product worktree. Exit codes are the process status.

- `python3 scripts/test_memory_layers.py` exit 0. Default rung info exit 0; warn exit 1; error exit 2; absent rung exit 0. `gist_parent` and `frame_members` reported at info and not failures. Protostar without a gist has no `missing_gist`.
- `python3 scripts/test_validation_warnings.py` exit 0.
- `python3 scripts/test_activation_cards.py` exit 0.
- `python3 scripts/test_help_paths.py` exit 0.
- `python3 scripts/release_readiness.py` exit 0. `package_version: 0.13.0`, `version_consistency: pass`.
- `python3 scripts/run_tests.py` exit 0. All 16 repository test entrypoints passed.
- `python3 scripts/atlas.py compile --root <atlas-atlas> --json` exit 0. `ok` true. critical 0. warnings 0. info 468 (`legacy_document` 167, `missing_gist` 301), severity info. The store has no `memory` block, so the rung is info.

## Changed files

- `.github/workflows/atlas-compile.yml`
- `CHANGELOG.md`
- `README.md`
- `SKILL.md`
- `apm.yml`
- `references/SCHEMA.contract.json`
- `references/ci/github-actions.caller.yml`
- `references/ci/github-actions.compile.yml`
- `references/help/VERSION`
- `references/help/getting-started.md`
- `references/help/index.md`
- `references/paths/memory-migrate.md`
- `references/paths/query.md`
- `references/paths/remember.md`
- `references/paths/schema.md`
- `references/scenarios/memory-layers-adversarial-v1.yaml`
- `references/templates/frame.md`
- `references/templates/gist.md`
- `references/templates/page.md`
- `scripts/atlas_cli/__init__.py`
- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/init.py`
- `scripts/atlas_cli/commands/schema_cmd.py`
- `scripts/atlas_cli/commands/validate.py`
- `scripts/atlas_cli/core/overlay.py`
- `scripts/test_activation_cards.py`
- `scripts/test_memory_layers.py`

## Outcome

The skill pull request is open. This store was not hand-edited at SCHEMA.json and was not opted into warn or error.
