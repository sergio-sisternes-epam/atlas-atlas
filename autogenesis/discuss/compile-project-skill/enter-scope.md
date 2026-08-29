---
type: document
title: "Orbit — when must Atlas Enter be path compile?"
created: 2026-08-27
work_id: 2026-08-27-compile-project-skill
status: settled
kva: alive
reality: current
description: "Settled E2: path compile only when compile is the work. Operator 2026-08-27."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-project-skill/path-id.md
    kind: follows
  - path: work/2026-08-27-compile-project-skill.md
    kind: implements
  - path: autogenesis/discuss/compile-project-skill/hub.md
    kind: related
---

## Content

`path: compile` exists. Remember, work, landscape, and Autogenesis discuss already run `atlas compile` as a tool at the end of a write. Autogenesis also forbids silent path→path invokes (one path at a time).

### Options

**E1 — Card must be `path: compile` before any `atlas compile` CLI.**  
Strict. Other paths cannot compile without re-issuing Enter. Collides with remember/work/landscape/discuss already compiling on their own path.

**E2 — Card is `path: compile` only when compile is the work.**  
Focused repair, session close-out, schema/contract repair walks. Other paths may call the CLI as a **tool** if they follow the contract in `paths/compile.md` (focused while editing, unfocused at session close, no green-lens-as-close). No second Enter.

**E3 — Other paths substrate-load `paths/compile.md` before their compile step, card path unchanged.**  
Same nesting contract Autogenesis uses for skills. Heavier than E2. Clearer than folklore. Still not a second Enter.

### Tension

E1 makes compile undeliverable inside current write paths unless Autogenesis one-path rule is waived for compile. E2 is how `atlas search` already sits under `path: query` — other paths sometimes search without becoming query. E3 is the honest middle if the compile module is the only place the related-files rule may live.

### Not this orbit

Related-files definition. Implement. Extra CLI flags.

## Answer (operator 2026-08-27)

**E2.** `path: compile` only when compile is the work. Other paths may use the CLI as a tool. E1 and E3 are alternative, not current.

## Batch

1. Settled E2.
2. Moved to `tool-lenses.md`.
