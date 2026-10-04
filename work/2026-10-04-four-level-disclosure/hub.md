---
type: work
title: Four-level progressive disclosure for Atlas memory
created: 2026-10-04
work_id: 2026-10-04-four-level-disclosure
status: settled
kva: alive
reality: current
origin: user
sensitivity: internal
description: Discussion hub for the four-level memory write model. Objective is an updated model that fixes one-schema-per-folder.
discussion_root: work/2026-10-04-four-level-disclosure/hub.md
current_branch: work/2026-10-04-four-level-disclosure/evolve-areas.memory.md
relates_to:
  - path: autogenesis/plans/2026-10-04-four-level-disclosure.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/four-level-disclosure.schema.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/theory.memory.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/counters.memory.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/evolve-areas.memory.md
    kind: records
  - path: work/2026-10-04-four-level-disclosure/stamp-beta4.memory.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/one-gist-counts.memory.md
    kind: related
---

## Scope

Subject: four-level progressive disclosure for Atlas memory. Objective: an updated memory model that fixes the one-schema-per-folder concern. This hub is the discussion root. It does not move. The live branch after the retrospective pass is the evolve-areas record.

This store's contract is unstamped SCHEMA.json. Stamp shape is shipped beta (frame, gist, page). It cannot express type schema. Pages below use the closest legal types: frame for the schema, gist for cluster summaries, page for memories. No new engine was invented.

## Status

Settled as a discussion record. Not implement authority. Product code and a product pull request are out of scope. current_branch is the evolve-areas memory, which records the conclusion.

## Outcomes

- Recall should walk index, schema, gist, memory and stop when the level answers.
- Remember should refuse to finish until gist, schema, and index are updated.
- Migrate should build that stack, allow more than one schema when the subject changes, and drop leftover frame.md.
- Compile should fail on a gist with no schema, a schema missing from the index, or an upper page that describes a memory that no longer says that.
- Contract and skill text should name this write model.
- Discuss should file several schemas when the subject changes.

## Batch

Claims engaged: the four-level stack; index as a hot schema cue list rather than laboratory STM or a table of contents; one gist still counts; contract stamp 0.13.0-beta.4 is not re-opened. Counters kept, not deleted. No surviving pending was left as a catalog bullet. No protostar was required.
