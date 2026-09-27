---
type: document
title: "Orbit — local validation versus store certification"
created: 2026-09-14
work_id: 2026-08-27-compile-project-skill
status: settled
kva: alive
reality: current
description: "Operator-selected replacement for L1: write paths may use --path for local validation; close-out and CI remain unfocused."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/plans/2026-08-27-compile-project-skill.md
relates_to:
  - path: autogenesis/discuss/compile-project-skill/tool-lenses.md
    kind: counters
  - path: autogenesis/discuss/compile-project-skill/hub.md
    kind: related
  - path: work/2026-08-27-compile-project-skill.md
    kind: implements
---

## Content

The observed failure is not a missing CLI lens. Agents are following the
settled L1 instruction and recompiling the whole Atlas after each small write.
The instruction optimises for one undifferentiated health claim and makes the
cheap edit loop pay the cost of store certification repeatedly.

The operator selected a two-level contract:

1. **Local validation:** after a small write, use
   `atlas compile --root <atlas> --path <changed-file-or-folder>`.
2. **Store certification:** at discussion or session close, and in CI, run
   unfocused `atlas compile --root <atlas>`.

`--type` remains outside ordinary write paths. A logical change can cross page
types, so a type lens can hide related work nodes, decisions, or protostars.

For a write that changes several pages, the local `--path` is the narrowest
common ancestor folder of all files in that coherent write batch. The rule is
path-based rather than graph-based: local validation does not calculate or
compile `relates_to` neighbours.

If that common ancestor is the Atlas root, local validation is an unfocused
compile. The batch is store-wide and must pay the store-wide validation cost.

The first adoption scope is the Atlas package contract only. Autogenesis,
Discuss, and other caller skills that repeat unfocused compile instructions
will adopt the contract in later, separately governed changes.

Within Atlas, the root contract defines the distinction and the `remember`,
`work`, and `landscape` paths apply it directly. CLI help alone is
insufficient because those path procedures currently instruct agents to run
an unfocused compile after each write.

Structural paths such as `schema`, `configure`, and `migrate` remain
unfocused after each material change because they can alter validation
semantics or whole-store structure.

This counters L1 on `tool-lenses.md`. It retains L1's safety boundary at
close-out while removing repeated whole-page walks from the interactive loop.

## Settled contract

1. `remember`, `work`, and `landscape` locally validate the narrowest common
   ancestor folder of the coherent write batch with `--path`.
2. A root common ancestor becomes an unfocused compile.
3. `--type` is not an ordinary write-path lens.
4. Discussion/session close and CI always run an unfocused compile.
5. Structural paths remain unfocused after material changes.
6. This change updates Atlas only; caller packages adopt later.

## Ready for design

The existing plan pins L1 and therefore cannot be implemented as written. A
formal design Run must supersede L1, update the Atlas root contract plus
`remember`, `work`, and `landscape`, preserve unfocused certification, and
leave caller-skill adoption out of scope.
