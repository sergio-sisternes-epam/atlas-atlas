---
type: decision
title: "Atlas recommended types align with agentic memory roles"
created: 2026-08-23
status: accepted
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "experience=episodic, decision=semantic pin; lesson/recipe optional; memory is not a page type."
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: experiences/2026-08-23-okf-wiki-design-challenge-karpathy-realign.md
    kind: derived_from
  - path: experiences/2026-08-23-atlas-design-plan.md
    kind: implements
  - path: decisions/atlas-name.md
    kind: related
---
## Decision

Recommended SCHEMA types are `experience`, `decision`, `lesson`, and `recipe`. Atlas is the memory substrate; pages are not typed `memory`.

## Rationale

Matches AI agent episodic / semantic / procedural vocabulary while keeping human-friendly names and existing templates.

## Alternatives considered

Using `memory` as a page type, or renaming experience to mean distillation, was rejected after think-challenge against cognitive science and agent-memory literature.

## Consequences

Opening-test promotes use experience for sessions and decision for pins; lesson/recipe templates deferred until needed.

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **derived_from:** [2026-08-23-okf-wiki-design-challenge-karpathy-realign](../experiences/2026-08-23-okf-wiki-design-challenge-karpathy-realign.md)
- **implements:** [2026-08-23-atlas-design-plan](../experiences/2026-08-23-atlas-design-plan.md)
- **related:** [atlas-name](atlas-name.md)
