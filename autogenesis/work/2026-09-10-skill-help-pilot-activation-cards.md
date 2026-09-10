---
type: decision
title: "Show intent and actual Atlas use on both help activation cards"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: accepted
kva: alive
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: autogenesis/work/2026-09-10-skill-help-pilot-decisions.md
    kind: follows
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: related
---

## Decision

Both help and getting-started must have activation cards highlighting the
user's intent and the Atlas used. This requirement was explicitly requested
after the formal pilot design was captured.

## Rationale

The user should be able to see which explanatory path is active and where the
answer's knowledge came from. A selected/default store is not evidence that
the assistant consulted it or used its content.

The plan's proposed mechanism separates selected id/root from actual
atlas_used, refreshes provenance after retrieval, and explicitly marks
baseline-only responses. These mechanics and their probes are design details,
not a claim of installed runtime behaviour. No new mounting or writing authority
is implied. The overall implementation plan remains awaiting approval.

## Provenance

User turn, 2026-09-10 at 15:08 +01:00, project session
9d0a896f-fb3f-4f6d-a84e-8014e2ab4231:
"Add activation cards to help and getting-started, highlighting the intent and the atlas used".

## Changed files

This design amendment changes only subject-store knowledge:

- autogenesis/plans/2026-09-10-skill-help-pilot.md
- autogenesis/work/2026-09-10-skill-help-pilot-activation-cards.md
- autogenesis/work/2026-09-10-skill-help-pilot.md
- autogenesis/work/index.md
