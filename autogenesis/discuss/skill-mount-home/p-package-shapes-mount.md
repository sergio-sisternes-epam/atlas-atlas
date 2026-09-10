---
type: protostar
title: "Package-shapes still mounts atlas-atlas at skill references/atlas"
created: "2026-09-03"
status: probed
kva: forming
growth: true
star_kind: tension
origin: derived
sensitivity: internal
description: "decisions/package-shapes.md still says this skill mounts the dedicated store at references/atlas. Not superseded in this pass."
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: derived_from
  - path: decisions/package-shapes.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/exit-skill-internal-store.md
    kind: related
---

## Pending

Answered: `decisions/mount-dot-atlas-submodule.md` supersedes package-shapes mount-at-references/atlas. Atlas 0.8.5 implements it.

## Origin

Operator: git-mesh and everything else should use `.atlas`. Package-shapes was not on the exit ramp this turn.
