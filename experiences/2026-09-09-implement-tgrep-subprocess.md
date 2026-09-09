---
type: experience
title: "Implement tgrep argv subprocess coarse driver"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: closed
description: "Enabled atlas:tgrep as digest-keyed argv index/search. Never serve. Missing binary and serve.json fail closed."
origin: derived
sensitivity: internal
implements: 2026-09-09-atlas-smr-configurable-recall
closes: []
plan_path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
construct_eval: deferred
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: derived_from
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
---

## Context

User asked how to enable tgrep after SMR landing. Selected: relax subprocess,
rebuild a local tgrep index on digest mismatch, never serve. Capture the pin
and implement.

## What happened

Product `tgrep` driver now locates `PATH` tgrep, indexes into
`.atlas-index/tgrep/`, searches with `--json -F --index-path`, and post-filters
to admitted pages. `serve` and `--no-index` are rejected before exec.

## Changed files

- `scripts/atlas_cli/core/drivers/tgrep.py`
- `scripts/atlas_cli/core/recall.py`
- `scripts/atlas_cli/core/recall_config.py`
- `scripts/test_recall_config.py`
- `scripts/test_recall_pipeline.py`
- `references/paths/configure.md`
- `CHANGELOG.md`
- `autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md`
- `experiences/2026-09-09-implement-tgrep-subprocess.md`
- `work/2026-09-09-atlas-smr-configurable-recall.md`
- `autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md`
- `autogenesis/discuss/recall-architecture/hub.md`

construct_eval deferred: no new subject-skill adversarial fixture in this
follow-on; unit and pipeline tests cover fail-closed paths.

## Lesson

Disk-only tgrep is still stale unless Atlas owns rebuild. Daemon detection
must fail closed because search auto-connects to `serve`.
