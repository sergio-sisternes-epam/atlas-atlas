---
type: decision
title: "Consuming skills declare their Atlas through a mount activation card"
created: "2026-09-03"
status: settled
work_id: "2026-09-03-skill-mount-home"
kva: alive
description: "Init and migrate stamp one exact Atlas mount card into the consuming skill's main SKILL.md; no copied module or local registry row."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: decisions/mount-dot-atlas-submodule.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/p-enter-card-shape.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/pin-stamp-skill-enter.md
    kind: derived_from
---

## Decision

A skill that uses Atlas declares its process-memory store in the skill's main
`SKILL.md` with this exact activation card:

```text
skill: atlas
path: mount
path_module: <atlas-skill>/references/paths/mount.md
atlas_id: <this skill’s host/org/repo>
ref: main
```

The card is the durable reference. `atlas-mesh.json` remains the active
repository's mount catalogue, not the consuming skill's declaration.

Atlas paths `init` and `migrate` must stamp this card idempotently. They
recognise or update an equivalent card instead of creating duplicates. If the
main `SKILL.md` is absent or cannot be updated, they fail visibly and do not
claim completion.

## Boundaries

- `path_module` points to the loaded Atlas skill. The consuming skill does not
  copy `mount.md`.
- The consuming skill does not need an additional path-registry row for
  `mount`.
- Do not add `references/atlas.md` as a pointer.
- Do not keep or create a process-memory store under
  `<skill>/references/atlas`.
- Mount resolves the store under the active repository at
  `.atlas/<atlas_id>/`.

## Implementation state

The declaration shape is settled. Atlas 0.8.5 has generic `mount`, `init`, and
`migrate` paths, but `init.md` and `migrate.md` still need the explicit,
idempotent `SKILL.md` stamping step before this work closes.

