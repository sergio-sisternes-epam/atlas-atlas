---
type: protostar
title: "How does APM materialise a skill Atlas without dropping git remotes?"
created: 2026-08-29
status: open
kva: forming
reality: current
growth: true
star_kind: tension
description: "APM drops git remotes. Repair is Atlas CLI + agent, not an APM hook. See atlas-apm-uncoupled.md."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: related
---

## Growth path

Keep `references/atlas` as the in-skill path. After APM copies the skill into the harness tree, that folder should still be a git checkout (submodule or atlas install) with a remote, so edits can PR.

## Open question

APM will not learn Atlas. After the skill lands in a harness folder, the agent runs Atlas verbs so `references/atlas` is a git checkout again. Remaining question: exact verb sequence (`install` vs `init` in an existing folder).

## Origin

APM cycle vs successful in-place Atlas edits.
