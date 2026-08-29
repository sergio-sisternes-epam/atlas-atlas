---
type: document
title: "Orbit — related files for a focused compile"
created: 2026-08-27
work_id: 2026-08-27-compile-project-skill
status: settled
kva: alive
reality: current
description: "Settled R3 + 1-hop outgoing. Close-out unfocused via D1."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-project-skill/tool-lenses.md
    kind: follows
  - path: work/2026-08-27-compile-project-skill.md
    kind: implements
  - path: autogenesis/discuss/compile-project-skill/hub.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/leaves/p-compile-project-skill.md
    kind: derived_from
---

## Content

`path: compile` is the only path allowed to pass `--path` / `--type`. The origin protostar left “related files” undefined: same folder, `relates_to` neighbours, or work-cluster.

0.7.6 `--path` is a **store-relative prefix or one file**. It does not walk edges. Any richer “related” rule is agent procedure on top of that flag (possibly several compile invocations), not a new CLI flag this work.

### Options

**R1 — Prefix only.**  
Agent picks `--path <folder-or-file>` for the slice under edit. No duty to follow `relates_to` or `work_id`. Honest about what 0.7.6 can do. Misses a work hub sitting in `work/` while you edit `autogenesis/discuss/…`.

**R2 — Prefix plus work cluster.**  
If pages carry a `work_id`, also compile `--path work/<work_id>.md` (and the plan path if known). Two (or three) focused compiles. Still no general graph walk.

**R3 — Prefix plus `relates_to` neighbours.**  
After the first focused compile, walk frontmatter edges and compile each neighbour path. Closest to “related files”. Cost and cycle risk. Edges can point across the store; this can become an unfocused compile in disguise.

**R4 — No related-files rule in v1.**  
`--path` means what the CLI means. Document that focused compile is a slice, not a cluster. Session close (unfocused) is the completeness check. Smallest design.

### Close-out (Q2)

Origin protostar: session close is unfocused. That now applies to `path: compile` itself, not to write paths (those are always unfocused under L1).

### Not this orbit

New CLI flags. Implement. Globs / repeatable `--path`.

## Batch

1. R1, R2, R3, or R4?
2. Confirm: `path: compile` session-close is always unfocused, even after a green focused slice?
