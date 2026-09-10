---
type: decision
title: "Query Atlas for reference gaps and disclose unavailable knowledge"
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
  - path: autogenesis/work/2026-09-10-skill-help-pilot-activation-cards.md
    kind: follows
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: related
  - path: atlas-project/vision.md
    kind: derived_from
  - path: atlas-project/branching-model.md
    kind: derived_from
---

## Decision

If references lack information needed to answer the actual help question,
query Atlas. If retrieval fails for any reason, explicitly tell the user that
help is limited and the Atlas knowledge store containing fuller information
is unavailable for this answer. Include the known reason; do not silently
replace missing evidence with general model knowledge.

This refines "optional enrichment": an Atlas is not required to read supported
baseline help, but retrieval is required when that baseline cannot answer.
Partial coverage also counts as a gap. A failed prerequisite is an explicit
inability to query, not a successful search.

## Rationale

In the 2026-09-10 help rehearsal, "Why is atlas using git?" received general
Git benefits instead of Atlas's documented rationale. The user challenged
reference sufficiency. The assistant then queried the mounted Atlas and read
vision.md, branching-model.md and sdlc-first.md. They explain knowledge evolving
through branches, teams consuming pinned understanding and contribution through
pull requests. The fuller explanation differed materially from generic Git
mechanics.

The user then explicitly required this fallback and failure disclosure.
The observed lookup succeeded; no outage or failed-query behaviour was actually
tested. The formal plan adds failure fixtures, not fabricated results.

## Disclosure boundary

A successful search with no relevant evidence is a knowledge gap, not an
unavailable Atlas. If only part of the evidence can be accessed, report the
failed part and retain citations for the supported part. Do not claim that an
unseen source is guaranteed to contain the answer.

Read-only help still does not authorise mounting, authentication changes,
repairs, installs or publication. Activation cards and prose must agree on
actual Atlas use and limited versus complete help.

## Provenance

User turns at 15:31 and 15:33 +01:00, 2026-09-10, project session
9d0a896f-fb3f-4f6d-a84e-8014e2ab4231.
Executed queries: "git source of record path:atlas-project", then the bounded
title-grounded rewrite "git source of record branching knowledge grows path:atlas-project".
Pages read: atlas-project/vision.md, atlas-project/branching-model.md,
atlas-project/sdlc-first.md. This is a recorded rehearsal and user decision,
not an implemented help-path evaluation or approval of the whole plan.

## Changed files

- autogenesis/plans/2026-09-10-skill-help-pilot.md
- autogenesis/work/2026-09-10-skill-help-pilot-reference-gaps.md
- autogenesis/work/2026-09-10-skill-help-pilot.md
- autogenesis/work/index.md
