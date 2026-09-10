---
type: document
title: "Pin — move both skill-internal and subject/project write-homes"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "For this orbit, every Atlas write-home is the active repository. Reopens the git-mesh skill-internal exception without yet retiring it."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-objective.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: counters
---

## Content

Operator pinned: move **both** write-homes into the active repository — skill-internal memory and subject/project Atlases.

Project corpora already default to `.atlas/<encoded-id>/` when the parent is git. The new work is the skill-internal exception: `<skill>/references/atlas` would no longer be the write-home, even for that skill’s own atlas-id.

This orbit now treats the exception as in play. The git-mesh decision page stays settled until a later pin supersedes it. This page does not implement the move.

### Outcome

KVA alive. Live distinction is what the skill path becomes if it is no longer the store: pointer plus mount-if-missing, or something else, and whether that kills path-as-signal.
