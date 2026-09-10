---
type: protostar
title: "Source-traceable skill help: pending pattern extraction"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: open
kva: forming
growth: true
star_kind: refine
stage: design
artifact: autogenesis/plans/2026-09-10-skill-help-pilot.md
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: derived_from
  - path: autogenesis/work/2026-09-10-skill-help-pilot-experience.md
    kind: derived_from
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: derived_from
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
---

## Pending

Formal design now lives at
[the pilot plan](../plans/2026-09-10-skill-help-pilot.md). This node retains
the original discussion below and tracks one remaining question: whether
source-traceable skill help deserves extraction beyond an Atlas-local design.

Before extraction, collect repeated implemented uses, including a different
skill/context, actual baseline-versus-enrichment results, failure cases, source
freshness behaviour and retrieval cost. Compare the candidate with Genesis
C1/C6/B2/S4/S7 and Autogenesis B17; admit only a genuine additional pattern.
One conversational rehearsal plus a formal plan is insufficient evidence.

No active catalogue entry or implementation authority is created here. The
historical candidate fields below are not the current implementation contract.

## Original discussion proposal

Candidate behaviour for discussion, not a finished behavioural contract:

- getting-started explains purpose, prerequisites and a shortest useful first
  journey, then points to relevant path help.
- help with no target shows supported paths; help for a named path explains
  intent, inputs, prerequisites, examples, outputs, side effects and boundaries.
- Both explain rather than execute the described operation. Reading help for
  mount, init or remember must not itself authorise that operation.
- Ship a baseline with the skill. A candidate Atlas source record identifies
  repository, immutable revision, file path and applicable skill version.
  Pins provide traceability, not evidence that the content is correct.
- Keep capability claims grounded in the installed reference. Add clearly
  labelled, cited Atlas examples and lessons only when relevant and compatible.
  Unknown, stale or conflicting versions require an explicit qualification.
- Begin enrichment with the subject Atlas. Expansion into another relevant,
  authorised Atlas should be bounded; a universal cross-Atlas crawl is not
  implied by the user's idea.
- Missing Atlas access must leave baseline help usable, with enrichment
  unavailable stated honestly. An Atlas source pin is not a runtime prerequisite
  for a user's first help request.

## Candidate probe

User-pinned content correction from the live walkthrough: storage guidance must
include a branch in an existing repository as a convenient way to get started.
A dedicated repository is also valid; the choice is a user preference. Do not
imply that creating another repository is required or inherently preferable.
Explain the selected branch/ref when describing how to connect the store.

Compare baseline-only and enriched answers for a first-use request and one
path-specific request. Include no mounted Atlas, a compatible lesson, a newer
incompatible source, an unknown path, and help for a mutating path.

Look for a correct first next step, no invented capabilities, traceable added
claims, and no execution of the operation being explained. Compare usefulness
against retrieval cost. These are proposed probes, not executed results or
approved acceptance criteria.

## Origin

### Candidate curated help knowledge, 2026-09-10

The user proposed an atlas-help schema in the subject Atlas, with wiki pages
distilled from learnings and linked to wider Atlas content. This extends the
bundled-reference agreement; it does not replace the offline baseline.

Proposed three-layer structure:

1. Bundled skill reference describes supported behaviour for the installed
   version and remains usable without an Atlas.
2. A curated help/ section in the resolved subject Atlas provides onboarding,
   per-path explanations, FAQs and troubleshooting. It links to baseline source
   records and underlying lessons, decisions and experiences.
3. Wider relevant Atlas content supplies additional evidence and contextual
   examples when the curated pages are insufficient.

An optional atlas-help schema overlay could add a distinct help-page type with
required provenance and applicability metadata. Schema validates structural
requirements, not factual correctness, content freshness or answer authority.
Do not redeclare core document/recipe types or claim a free-layout help folder
merely because pages live there. Any actual overlay installation requires the
Atlas schema CLI and formal design approval for this new surface.

Candidate page metadata: subject skill, topic or activation path, applicable
skill version, guidance status, baseline source revision and supporting
relates_to edges. Keep getting-started and general help topics possible without
requiring every page to identify a single operational path. Intra-store links
should point to evidence rather than duplicate its full text; cross-store
evidence needs an explicit external source reference.

The branch-versus-dedicated-repository correction is the first proposed example:
distil it into a user-facing storage explanation while preserving the original
feedback and grounding technical claims in the supported mount/ref contract.
Not every conversation is ready for publication. Retrieval must distinguish
candidate learning from current guidance and version-incompatible material.

These were unapproved discussion candidates. The formal plan now pins a
proposed pilot contract for review. No schema or help pages were installed.

The user pinned Atlas-first scope and a bundled baseline with optional
enrichment. The storage-location correction above is also explicit user feedback. The
remaining boundary and evaluation details are agent proposals. Keep them
forming until discussed or taken into formal design.
