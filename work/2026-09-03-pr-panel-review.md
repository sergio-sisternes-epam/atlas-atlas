---
type: work
title: "Project-level Copilot PR panel-review skill"
created: 2026-09-03
work_id: 2026-09-03-pr-panel-review
status: done
description: "Delivered an APM-authored Atlas panel-review skill after a direct Copilot Code Review experiment proved repository skills cannot replace CCR orchestration or output."
origin: user
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/plans/2026-09-03-pr-panel-review.md
    kind: related
  - path: experiences/2026-09-03-implement-code-review-skill.md
    kind: related
  - path: experiences/2026-09-03-pivot-panel-review-to-apm.md
    kind: related
  - path: decisions/panel-review-apm-over-copilot-code-review.md
    kind: related
---

## Scope

Author an Atlas-specific advisory panel with four review lenses plus a synthesizer. Preserve evidence from the first direct Copilot Code Review implementation, then deliver the final APM-authored `panel-review` skill and generated Copilot deployment.

Automatic replacement of Copilot Code Review's built-in pipeline remains out of scope because repository skills are supplementary context. Custom `.agent.md` personas and org-wide installation remain future design work.

## Status

**done** — direct CCR attempt evaluated and superseded; APM source, generated Copilot deployment, lockfile, package metadata, documentation, and adversarial scenario shipped in PR 7. Memory records the incomplete formal redesign gate for the pivot.

## Outcomes

- Superseded direct CCR attempt: `experiences/2026-09-03-implement-code-review-skill.md`
- Replacement decision: `decisions/panel-review-apm-over-copilot-code-review.md`
- Final APM implementation: `experiences/2026-09-03-pivot-panel-review-to-apm.md`
- Authored source at `.apm/skills/panel-review/`; generated Copilot target at `.agents/skills/panel-review/`
- Final adversarial scenario: `references/scenarios/panel-review-adversarial-v1.yaml`

## Related

Historical plan: `autogenesis/plans/2026-09-03-pr-panel-review.md`.

The plan was implemented and then superseded by explicit operator direction. The decision and both implementation experiences preserve the change of direction without rewriting the original design.
