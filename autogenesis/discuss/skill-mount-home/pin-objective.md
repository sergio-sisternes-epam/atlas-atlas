---
type: document
title: "Pin — Atlas writes stay under the active repository"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "Locked objective for skill-mount-home. Does not yet change the git-mesh skill-internal exception."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/global-skill-out-of-repo.md
    kind: follows
---

## Content

Operator pinned the objective:

Keep Atlas writes under the active repository’s control, so a globally installed skill cannot become an untracked write-home.

This locks evaluation for the rest of the orbit. It does not by itself retire `references/atlas` as skill-internal memory. That exception is still current reality until a later pin reopens it.

### Outcome

KVA alive. Next batch item is which write-home we are moving: skill-internal memory, subject/project Atlas, or both.
