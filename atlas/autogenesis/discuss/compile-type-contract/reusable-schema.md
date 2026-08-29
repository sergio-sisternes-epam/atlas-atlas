---
type: document
title: "Orbit — reusable Atlas: how every store gets a valid schema"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Operator questions: enforce SCHEMA on every Atlas we create; whether atlas needs a schema path. Not implement."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/unconstrained-types.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/leaves/p-contract-vs-live-schema.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

C/D/E on which types get a `by_type` block stays open on `unconstrained-types.md`. This orbit is the reusable-skill problem.

### Current reality

Atlas is already multi-store. Each skill can have `references/atlas/SCHEMA.json`. Compile takes `--root`. There is **no** `atlas init`. There is **no** schema path. Path registry is query, remember, work, landscape.

A new folder without `SCHEMA.json` fails compile (`schema_present`). That is a gate, not a factory. Nothing writes the first SCHEMA or copies `templates.by_type` into the new root.

Skill-level templates live at `atlas/references/templates/` (experience, decision, work, document). Protostar template exists only under **this** store’s `templates/`. A new Atlas seeded from the skill templates would not even get a protostar markdown template.

When this skill adds a type contract, existing sibling stores (discuss, autogenesis, medium, …) do not upgrade. Compile will not tell them their SCHEMA is stale relative to the skill.

### Question 1 — how do we enforce SCHEMA create/update on any Atlas we create?

Three layers, not one trick:

1. **Birth** — an init/bootstrap step writes a SCHEMA that Layer 1 accepts (root fields + default `templates.by_type` from the skill). Autogenesis “Initiate Atlas” must call that step, not hand-write JSON.
2. **Gate** — `atlas compile --root` Layer 1 on every store. Invalid or missing SCHEMA is already critical. After this work, “recommended type with no by_type and not marked unconstrained” is a Layer 1 miss (warning first, per pin A).
3. **Evolve** — when the atlas *skill* ships a new contract (protostar `by_type`), sibling stores need an explicit upgrade, not silent mutation. Compile can warn “skill contract version ahead of store SCHEMA”; a path performs the merge.

We do not auto-edit other skills’ SCHEMA.json. Reuse is “same CLI + same path + same contract file”, not a phone-home rewrite.

### Question 2 — do we need an atlas path for schema expertise?

Lean: **yes.** Compile is a tool. Paths are the agent procedure. Remember tells you how to write a page; nothing tells you how to add a type to SCHEMA, init a root, or upgrade an old store.

The path is not a new catalog skill. Candidate name `schema` (or `bootstrap` if we split birth from evolve — one path unless the procedure splits in design).

In that path, not in SKILL.md prose only:

- init a root from SCHEMA.contract + default templates
- validate Layer 1 (definitions valid)
- add or tighten a `by_type` block without breaking the simplicity budget
- mark a recommended type unconstrained on purpose
- upgrade a store SCHEMA when the skill contract moved
- stop and hand format-only questions to **okf**

OKF stays the floor (frontmatter, non-empty type, unknown types legal). Atlas schema path owns `templates.by_type`, compile checks, and store birth.

## Provenance

Operator turn: two questions on reusable enforcement and a schema path.
