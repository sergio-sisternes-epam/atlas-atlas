---
type: decision
title: "Pin — exact consuming-skill Atlas Enter card"
created: "2026-09-03"
status: settled
kva: alive
origin: derived
sensitivity: internal
description: "Init and migrate stamp this exact Atlas mount activation card into the consuming skill's main SKILL.md."
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-stamp-skill-enter.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/q-skill-atlas-reference.md
    kind: related
---

## Pin

`init` and `migrate` insert this exact activation card into the consuming
skill's main `SKILL.md`:

```text
skill: atlas
path: mount
path_module: <atlas-skill>/references/paths/mount.md
atlas_id: <this skill’s host/org/repo>
ref: main
```

`path_module` points to the loaded Atlas skill. The consuming skill does not
copy `mount.md`.

No additional path-registry row is required in the consuming skill. The card
is the durable declaration that identifies its Atlas and activates the Atlas
mount path.

Stamping must be idempotent: update or recognise an equivalent Atlas mount
card rather than inserting a duplicate.

If the main `SKILL.md` is absent or cannot be updated, fail visibly. Do not
claim init or migration completed without this declaration.
