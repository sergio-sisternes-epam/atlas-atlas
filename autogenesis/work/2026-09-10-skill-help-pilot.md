---
type: work
title: "Skill help pilot: bundled reference and Atlas enrichment"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: designed
kva: alive
stage: design
artifact: autogenesis/plans/2026-09-10-skill-help-pilot.md
plan_path: autogenesis/plans/2026-09-10-skill-help-pilot.md
approval: pending
origin: user
sensitivity: internal
description: "Formal Atlas help pilot design, observed lessons and pending pattern extraction."
relates_to:
  - path: decisions/cartograph-fork-in-atlas-exit.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph-experience.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: related
  - path: help/cartograph.md
    kind: related
  - path: help/open-cartograph.md
    kind: related
  - path: help/install-and-open-cartograph.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-reference-gaps.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-activation-cards.md
    kind: related
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-experience.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-decisions.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-lessons.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-proposal.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Scope

Original objective: test getting-started and help activation paths backed by
pre-built reference material, pinned as Atlas sources for traceability, and
enriched from relevant Atlases. These are proposed skill paths, not approved
new CLI subcommands or separate catalog skills.

## Status

Formal design persisted at the user's request on 2026-09-10; approval pending.
The linked plan is the current handoff, replacing informal proposals as the
design authority. Implementation has not begun. KVA alive denotes an active
work record, not evaluated product success.

The user selected an Atlas pilot first, a bundled baseline and optional Atlas
enrichment when references suffice. A later refinement requires Atlas retrieval
for reference gaps and explicit limited-help disclosure if retrieval fails.
A reusable Autogenesis pattern remains a candidate pending evidence.

## Outcomes

| Artifact | Role |
|---|---|
| [Design](../plans/2026-09-10-skill-help-pilot.md) | New-surface packet, pins, challenge, evaluation and backlog T1-T6 |
| [Experience](2026-09-10-skill-help-pilot-experience.md) | Observed walkthrough, correction and limitations |
| [Decisions](2026-09-10-skill-help-pilot-decisions.md) | Explicit user choices, separate from design recommendations |
| [Activation cards](2026-09-10-skill-help-pilot-activation-cards.md) | User-required intent and actual Atlas provenance on both help paths |
| [Reference-gap fallback](2026-09-10-skill-help-pilot-reference-gaps.md) | Mandatory query on insufficient references; visible limitations and Atlas unavailability on failure |
| [Cartograph memory](2026-09-10-skill-help-pilot-cartograph.md) | Current standalone package, Copilot-only activation boundary and reciprocal knowledge connection |
| [Old location exit](../../decisions/cartograph-fork-in-atlas-exit.md) | User-requested formal supersession of the historical in-Atlas Cartograph location |
| [Cartograph experience](2026-09-10-skill-help-pilot-cartograph-experience.md) | Native two-store opening, explicit reciprocal edges and the CLI/graph identity compatibility limit |
| [Curated visualiser help](../../help/index.md) | Authored overview, Canvas-menu opening and scoped APM installation instructions; no runtime routing implied |
| [Lessons](2026-09-10-skill-help-pilot-lessons.md) | Supported alternatives and version-qualified evidence |
| [Extraction candidate](2026-09-10-skill-help-pilot-proposal.md) | Pending repeated-use evidence and original discussion |

Implementation experience: none. Construct report: none. Behavioural Gherkin:
explicitly deferred because agent-spec is unavailable in the current session.
No active pattern was created. All artifacts remain in the subject Atlas.

The user subsequently requested concrete Cartograph knowledge and help.
Those pages now use the existing document type, with source pins and live
cross-store navigation to `atlas-cartograph-atlas`. A reciprocal connection
page lives there; primary pilot memory remains here. The consumer mounts
both stores, so future operations must select the intended Atlas explicitly.
The proposed Copilot-only `visualise` runtime path is an additional design
surface, not approval or implementation of the original pilot. No schema
overlay, package installation or global setting change is implied by these
knowledge deliverables.

The useful distinction is executable capability versus supplementary knowledge.
Bundled reference describes the installed skill. Retrieved examples and lessons
must not silently invent or upgrade its supported paths.

A cheap source comparison exposed real version skew: this repository's
SKILL.md at commit 3818586da56331949b03fe746ef21693d3c84169 declares version
0.10.0 and a configure path. The installed Atlas root loaded in this session
does not list configure. This motivates version-qualified help; it is not an
execution test of the proposed paths.

The Atlas query `getting-started help onboarding source authority` returned
adjacent recall, auth and CLI work, but no direct help-pattern precedent in the
returned hits. The glossary has no applicable help/onboarding aliases, so no
invented synonym rewrite was performed. The related memory-layers decision is
forming guidance, not proof of this pilot; it distinguishes historical episodes
from current guidance and supports examining source status.

## Provenance

- User conversation, 2026-09-10: initial idea and the two explicit scope choices.
- Repository source: https://github.com/sergio-sisternes-epam/atlas/blob/3818586da56331949b03fe746ef21693d3c84169/SKILL.md
- Installed source observed locally: /Users/sergio_sisternes/.agents/skills/atlas/SKILL.md.
  This observation is not an immutable pin of that installation.

## Discussion history

### Live walkthrough feedback, 2026-09-10

The user tried introductory help, mount help and storage-location help in this
conversation. On storage, the assistant recommended a dedicated repository but
omitted the option of using a branch in an existing repository. The user judged
the answer useful and explicitly corrected that omission: highlight an existing
repository branch as a convenient starting point, and present a dedicated
repository as an equally valid user preference rather than the default advice.
This is a content-quality finding from a conversational walkthrough, not an
implemented-path evaluation. No storage operation was requested by this feedback.

The user subsequently proposed an atlas-help schema and curated wiki pages in
the subject Atlas, distilled from learnings and linked to wider knowledge.
The proposal now preserves this possible middle layer between bundled
reference and wider retrieval. Overlay installation and publication rules remain
design candidates, not approved changes.

The original proposal preserves the discussion and now tracks future extraction.
The formal plan above contains the current pins and evaluation requirements.
Implementation still requires explicit approval of that plan.

## Earlier discussion receipt

Autogenesis discuss, Atlas mount/query/work/remember, Discuss speak/sprout/lint,
and OKF root instructions were loaded. Atlas search ran for
`getting-started help onboarding source authority`; pages read were glossary.md
and decisions/atlas-memory-layers.md, plus the installed and checkout skill
roots. No direct help-pattern precedent was established.

Atlas compile succeeded after persistence. Whole-store Discuss lint reported
existing L1/L4/L6 findings outside this pilot: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md,
atlas-project/partners/github-spec-kit.md, and work hubs for modular-graph-protocol,
compile-focus-lenses, compile-type-contract, landscape-review,
smr-configurable-recall and atlas-bm25-and-live-migration-v1. No pilot page was
reported. Those unrelated pages were not changed; no whole-store lint pass or
completed Autogenesis path is claimed.

## Formal design status

The later design Run loaded the design path, Genesis and the internal
think-challenge/patterns modules. Including the activation-card and reference-gap
amendments, it preserves nine sourced counters and their
dispositions, mini-genesis artifacts, a behavioural deferral and deterministic
evaluation mapping. It does not claim the earlier whole-store Discuss lint
findings were repaired. Design completion and publication are distinct: records
are persisted locally, with implementation and remote publication not performed.
