---
type: protostar
title: "Skill: how to compile a project Atlas effectively"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-focus-lenses
status: open
kva: forming
growth: true
star_kind: action
origin: user
sensitivity: internal
description: "Need a skill (or atlas recipe/path) that tells agents when to use focused compile vs a full close-out compile."
relates_to:
  - path: experiences/2026-08-27-implement-atlas-compile-focus-lenses.md
    kind: derived_from
  - path: work/2026-08-27-atlas-compile-focus-lenses.md
    kind: implements
---

## Pending

Author a skill (or an Atlas path/recipe if a whole skill is too much) that instructs project compile discipline now that `--type` and `--path` exist.

### While changing

Compile only the path under edit and related files. Use `atlas compile --root <atlas> --path <prefix>` (and `--type` when the slice is one type). Do not pay a whole-store page walk on every small edit. “Related files” still needs a rule: same folder, `relates_to` neighbours, or work-cluster only.

### Closing the session

Run a final unfocused `atlas compile --root <atlas>`. That is the check for breakage outside the lens (index rules, SCHEMA, pages you did not touch). Do not treat a green focused compile as session-close.

### Not this star

Implementing that skill. Extra compile flags. Changing 0.7.6 lens behaviour.
