---
type: experience
title: "Implement Atlas path ci and GitHub Actions adapters (0.8.13)"
created: 2026-09-03
work_id: 2026-09-03-atlas-ci-activation-path
status: closed
description: "Shipped the platform-neutral CI model, conformance checklist, GitHub reusable and copied adapters, and deterministic tests."
origin: derived
sensitivity: internal
implements: autogenesis/plans/2026-09-03-atlas-ci-activation-path.md
closes: 2026-09-03-atlas-ci-activation-path
plan_path: autogenesis/plans/2026-09-03-atlas-ci-activation-path.md
construct_eval: references/scenarios/ci-activation-adversarial-v1.yaml
relates_to:
  - path: work/2026-09-03-atlas-ci-activation-path.md
    kind: implements
  - path: autogenesis/plans/2026-09-03-atlas-ci-activation-path.md
    kind: related
---

## Context

Atlas mounts need an institutional merge gate that is distinct from both the
Atlas skill package's product CI and the agent-session `path: compile`.
Think-challenge exposed warning-gate noise, copied-workflow drift, private
cross-repository authentication, and workspace pollution.

## What happened

Atlas 0.8.13 adds path `ci` with a platform-neutral model and a checklist that
grades setups as missing, partial, incorrect, or correct. The approved v1.1
gate passes compile exit 0 and warning-only exit 1, retains JSON evidence, and
fails critical exit 2 or abnormal execution.

GitHub Actions has three shipped surfaces: a reusable `workflow_call`, a thin
mount caller, and a self-contained copied fallback. The adapters acquire the
pinned CLI under `RUNNER_TEMP`, use read-only permissions, SHA-pin third-party
Actions, reject `main` and `master` CLI refs, require `SCHEMA.json`, run
unfocused compile, and upload evidence even on failure.

## Outcome

Nine deterministic contract tests passed. YAML and embedded Bash parsed
successfully. The adversarial scenario records all approved counters.

compile defer: the full store reports six pre-existing
`atlas_uri_unmounted` warnings in historical git-mesh example pages; compile
returned `ok=true` with zero critical issues.

## Changed files

- `SKILL.md`
- `apm.yml`
- `.github/workflows/atlas-compile.yml`
- `references/README.md`
- `references/paths/ci.md`
- `references/ci/github-actions.compile.yml`
- `references/ci/github-actions.caller.yml`
- `references/scenarios/ci-activation-adversarial-v1.yaml`
- `scripts/test_ci_activation.py`
- `references/atlas/autogenesis/plans/2026-09-03-atlas-ci-activation-path.md`
- `references/atlas/autogenesis/plans/index.md`
- `references/atlas/work/2026-09-03-atlas-ci-activation-path.md`
- `references/atlas/work/index.md`
- `references/atlas/experiences/2026-09-03-implement-atlas-ci-activation-path.md`
- `references/atlas/experiences/index.md`
- `references/atlas/log.md`

## Related

The canonical model follows `atlas-project/branching-model.md`, which requires
compile on the contributor clone and again in CI.

## Follow-ups

Other CI platforms can implement the same M1-M10 clauses without copying the
GitHub adapter.
