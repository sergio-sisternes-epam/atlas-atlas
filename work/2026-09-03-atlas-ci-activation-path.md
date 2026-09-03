---
type: work
title: "Atlas path ci — canonical CI/CD for SCHEMA.json mounts"
created: 2026-09-03
work_id: 2026-09-03-atlas-ci-activation-path
status: done
description: "Activation path ci: platform-agnostic compile gate for any Atlas mount, GitHub Actions default adapter, conformance checklist."
origin: derived
sensitivity: internal
stage: done
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-ci-activation-path.md
    kind: related
  - path: atlas-project/branching-model.md
    kind: related
  - path: work/2026-08-27-compile-project-skill.md
    kind: related
  - path: experiences/2026-09-03-implement-atlas-ci-activation-path.md
    kind: related
---

## Scope

Add Atlas path `ci` so agents can assess, install, and repair CI/CD on any git repository that contains `SCHEMA.json`. Canonical model is platform-agnostic. Default adapter is GitHub Actions. Checklist grades missing, partial, incorrect, and correct setups.

Out of scope: Atlas skill package tests; path `compile` session discipline; other platform adapters.

## Status

done — 2026-09-03. Shipped in Atlas skill 0.8.5.

## Outcomes

- Plan: `autogenesis/plans/2026-09-03-atlas-ci-activation-path.md`
- Implement experience: `experiences/2026-09-03-implement-atlas-ci-activation-path.md`
- Canonical model and checklist: `references/paths/ci.md` in the Atlas skill
- GitHub Actions adapters: reusable workflow, thin caller, and copied fallback
- Construct contract: `references/scenarios/ci-activation-adversarial-v1.yaml`
- Deterministic contract tests: 9 passed

## Related

Branching model already says compile on the clone and again in CI. Path compile remains the agent-session gate.
