---
type: decision
title: "User-pinned scope and baseline for the Atlas help pilot"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: accepted
kva: alive
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: autogenesis/work/2026-09-10-skill-help-pilot-experience.md
    kind: records
---

## Decision

Start with an Atlas pilot, not a universal Autogenesis convention. Ship the
baseline reference with the skill and enrich from Atlas when available, so
newcomers do not need a working store just to learn how to start.

Present a branch in an existing repository as a convenient storage option
alongside a dedicated repository. Neither is inherently preferable; the user
chooses based on organisation and access needs.

Capture the work and experience now for possible future extraction. This is
not approval to implement the proposed design or admit a pattern.

## Rationale

The user explicitly chose the first two boundaries and corrected the storage
answer during the walkthrough. They later explicitly requested durable capture.
The curated-help/schema suggestion motivated formal design, but detailed
schema fields, eligibility rules and rollout tasks remain proposed.

## Provenance

Primary source: user conversation, 2026-09-10, recorded in the linked experience.
These are user preference/scope decisions, not claims of evaluated performance.
Technical support for ref-based mounting is in the source contract:
https://github.com/sergio-sisternes-epam/atlas/blob/3818586da56331949b03fe746ef21693d3c84169/references/paths/mount.md
