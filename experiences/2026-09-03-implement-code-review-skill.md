---
type: experience
title: "Implement project-level Copilot code-review skill"
created: 2026-09-03
work_id: 2026-09-03-pr-panel-review
status: superseded
origin: internal
sensitivity: internal
implements: 2026-09-03-pr-panel-review
plan_path: autogenesis/plans/2026-09-03-pr-panel-review.md
construct_eval: deferred
description: "Implemented the direct CCR skill, then learned from a real review run that repository skills supplement but do not replace Copilot Code Review orchestration or output."
relates_to:
  - path: work/2026-09-03-pr-panel-review.md
    kind: implements
  - path: autogenesis/plans/2026-09-03-pr-panel-review.md
    kind: related
  - path: decisions/panel-review-apm-over-copilot-code-review.md
    kind: related
  - path: experiences/2026-09-03-pivot-panel-review-to-apm.md
    kind: related
---

## Context

Approved plan `2026-09-03-pr-panel-review` after renaming Copilot dispatch from `pr-panel-review` to `code-review` (GitHub CCR changelog: create a `code-review` or similarly named directory).

## What happened

Created one project skill under `.github/skills/code-review/` with lazy lens assets. Roster: atlas-contract always-on; python-cli, skill-agent-contract, and security-gitops conditional. The orchestrator requested inline findings plus one advisory summary.

A real GitHub Actions review (`33755388569`, job `100648469257`) showed `EnableSkills=true`, one catalog entry, and invocation of `name="code-review"` from the PR head checkout. Despite that activation, CCR emitted its built-in approval overview and only one spelling comment. The skill was supplementary context, not control of CCR's orchestration or presentation.

## Outcome

The direct CCR implementation proved discovery and activation, but did not satisfy the requested deterministic panel output. It was removed and superseded by the APM direction.

## construct_eval

deferred: construct CLI (`/opt/homebrew/bin/construct`) raises `ModuleNotFoundError: No module named 'construct'`. Deterministic smokes matching the approved ids ran green by hand.

## Changed files

- `.github/skills/code-review/SKILL.md`
- `.github/skills/code-review/references/roster.md`
- `.github/skills/code-review/references/finding-schema.md`
- `.github/skills/code-review/references/synthesizer.md`
- `.github/skills/code-review/references/lenses/atlas-contract.md`
- `.github/skills/code-review/references/lenses/python-cli.md`
- `.github/skills/code-review/references/lenses/skill-agent-contract.md`
- `.github/skills/code-review/references/lenses/security-gitops.md`
- `references/scenarios/code-review-adversarial-v1.yaml`

## Related

Plan: `autogenesis/plans/2026-09-03-pr-panel-review.md`. Replacement decision: `decisions/panel-review-apm-over-copilot-code-review.md`.

## Follow-ups

The APM replacement and final result are recorded in `experiences/2026-09-03-pivot-panel-review-to-apm.md`.
