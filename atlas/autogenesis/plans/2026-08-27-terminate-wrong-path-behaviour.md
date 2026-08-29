---
type: plan
title: "Plan — terminate-wrong-path A+B"
created: 2026-08-27
work_id: 2026-08-27-terminate-wrong-path-behaviour
status: approved
description: "Approved design: discuss path terminate plus Atlas remember recipe. User approved A+B on 2026-08-27."
origin: user
sensitivity: internal
change_class: new-surface
kva: alive
relates_to:
  - path: work/2026-08-27-terminate-wrong-path-behaviour.md
    kind: implements
  - path: autogenesis/discuss/terminate-wrong-path/current-branch.md
    kind: derived_from
  - path: atlas-project/wrong-path-agent-memory-layer/exit-wrong-comparison.md
    kind: related
---

## Intent

When a discussion or remember turn shows the current frame is wrong, persist the wrong branch as terminated knowledge, write an alive exit-reason node, link that exit to the living vision or corrected thesis, and stop using the dead frame.

## Change-class

`new-surface` — new discuss path module plus Atlas remember recipe. Not a new skill.

## Scope

- Discuss path `terminate` as the KVA mechanism.
- Atlas remember recipe and hard-rule pointer so a remember agent cannot keep writing the dead matrix.
- Worked example remains `atlas-project/wrong-path-agent-memory-layer/`.

## Non-goals

- Silent agent terminate without explicit user correction.
- Deleting terminated pages.
- A sixth KVA value.
- Compile-enforced `kva_terminate` in this slice (lint L4 already exists).

## Pinned decisions

1. A+B. Discuss owns the exit ramp. Atlas remember loads that path via substrate contract.
2. Trigger is explicit user correction or explicit KVA terminate. No silent terminate.
3. Reshape edits an alive page. Supersede is for a frame that was fit. Terminate is never-fit or out of scope.
4. Exit-reason node must relate to an alive vision or correct-thesis page. Write one in the same persist if missing.
5. Archive notes may stay kva alive. The frame page is terminated.
6. Do not flip terminated to forming. Reactivation is a new page derived_from the stub.

## Challenge counters and pins

Zombie knowledge if old frames stay current — terminate and signal. Deleting rejected ideas blocks resurrection — keep the branch. Remember-only agents never load discuss — Atlas hook. Auto-unlearning without a human — user-explicit trigger only.

## Genesis Artifacts

Component: user trigger to Atlas remember to discuss terminate to terminated page plus exit-reason plus living thesis, then lint L4 and compile.

Sequence: detect trigger, query living thesis, load terminate, write pages, lint, compile, answer from living page only.

Cost: one extra path load per correction turn.

Acceptance: discuss registry lists terminate; Atlas remember and hard rules point at it; worked example still compiles.

## Catalogue Review

Terminate is a local sibling under discuss. Atlas recipe is an inline pointer. No second KVA implementation.

## Behavioural contract (agent-spec)

deferred: ship path text this Run; specify Gherkin is a follow-on protostar. Prose forbidden until then: silent terminate, delete terminated pages, answer from a terminated frame after the exit exists.

## Evaluation plan

Deterministic file presence and worked-example edges. Agent eval of trigger language later.

## Approval

User approved A+B on 2026-08-27. Implement follows in this thread.
