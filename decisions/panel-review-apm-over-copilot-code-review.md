---
type: decision
title: "Use an APM-authored panel review instead of customizing Copilot Code Review"
created: 2026-09-03
status: accepted
work_id: 2026-09-03-pr-panel-review
description: "Repository skills can inform Copilot Code Review but cannot replace its orchestration or output contract; use an explicitly invoked APM panel-review skill."
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-03-pr-panel-review.md
    kind: implements
  - path: autogenesis/plans/2026-09-03-pr-panel-review.md
    kind: supersedes
  - path: experiences/2026-09-03-implement-code-review-skill.md
    kind: records
  - path: experiences/2026-09-03-pivot-panel-review-to-apm.md
    kind: related
---

## Decision

Author the Atlas review panel at `.apm/skills/panel-review/` and deploy its Copilot-compatible copy to `.agents/skills/panel-review/` with `apm install --target copilot`.

Do not rely on `.github/skills/code-review/` to replace GitHub Copilot Code Review's built-in orchestration, approval overview, severity vocabulary, or comment-generation behavior.

## Rationale

The direct CCR experiment proved that the repository skill was discovered and invoked, but the resulting review still followed CCR's built-in pipeline. The requested behavior needs an orchestrator that owns isolated fan-out, inline comments, and exactly one Blocker/Recommended/Nits summary with expandable per-lens details.

An explicitly invoked APM skill provides a portable authored source, reproducible generated deployment, and a place to fail closed when isolated child threads are unavailable.

## Alternatives considered

- Keep the CCR skill and accept its native output: rejected because it does not guarantee the panel contract.
- Simulate all lenses sequentially in one context: rejected because it creates a panel-in-one-context contamination risk.
- Create one Copilot skill per lens: rejected because independent matching can produce unsynthesized comment streams.

## Consequences

- `.apm/skills/panel-review/` is authoritative; `.agents/skills/panel-review/` is generated.
- The panel is explicitly invoked rather than treated as a CCR output override.
- True isolated child threads are required; without them the panel reports that it cannot run.
- The original CCR plan remains as superseded historical evidence.
