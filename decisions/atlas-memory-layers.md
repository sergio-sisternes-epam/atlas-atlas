---
type: decision
title: "Atlas splits episodic log, current-theory slots, and a transform pass"
created: 2026-09-03
status: forming-guidance
work_id: 2026-09-03-human-memory-model
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: lessons/engram-not-file.md
    kind: derived_from
  - path: lessons/complementary-learning-systems.md
    kind: derived_from
  - path: lessons/consolidation-transforms.md
    kind: derived_from
  - path: lessons/reconsolidation-gated-update.md
    kind: derived_from
  - path: lessons/prediction-error-update-or-differentiate.md
    kind: derived_from
  - path: lessons/forgetting-is-expression-failure.md
    kind: derived_from
  - path: lessons/do-not-equate-immutability-with-correct-memory.md
    kind: derived_from
---

## Decision

Atlas memory has three layers, mapped from the human-memory cluster:

1. **Episodic log** — experiences and raw remember pages are append-only. Do not rewrite their claims in place.
2. **Current-theory slots** — decisions, recipes, and live lessons may **supersede**. A correction is a new page (or an explicit status flip plus a successor page) with `supersedes` / `contradicts`, not a silent edit of the old claim set.
3. **Transform pass** — compile, and later dream, may coarsen, index, and demote. Query answers from the current view. Forget defaults to stop expressing, not delete.

Promoting an episode into a current-theory slot requires agent thinking (query the old slot, design the new page, keep sources). Human approval is optional and only when the human asks for review on an important persist.

## Rationale

CLS forbids dumping every episode into the slow store at full speed. Reconsolidation evidence does not license unconstrained in-place rewrite. Forgetting research says expression and storage come apart. Immutability-as-trust fails when the stored sentence is wrong.

## Alternatives considered

- One append-only tree for every page: preserves history, poisons retrieval.
- In-place edit of every page: loses audit of what the agent used to believe.
- Hard-delete on forget: fights expression-failure evidence and legal/debug need to re-express.

## Consequences

Remember path should state the three layers. Query should not treat `superseded` / `terminated` pages as current guidance. Current-theory writes may run automatically after the agent designs the inventory. A human hold is available on request; it is not the default.
