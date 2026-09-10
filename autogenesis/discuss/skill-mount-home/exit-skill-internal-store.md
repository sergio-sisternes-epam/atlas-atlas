---
type: document
title: "Exit reason — skill-internal references/atlas store"
created: "2026-09-03"
kva_role: exit-reason
kva: alive
status: settled
reality: current
description: "Why decision-target-path is superseded, not terminated. Successor is decision-mount-dot-atlas-only."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: records
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/skill-mount-home/pin-objective.md
    kind: related
---

## Content

**Subject:** `autogenesis/discuss/git-mesh/decision-target-path.md`

**Against objective:** keep Atlas writes under the active repository’s control, so a globally installed skill cannot become an untracked write-home.

**Why supersede, not terminate:** that decision was fit in August. Clauses 1, 2, 4, and 5 still hold. Clause 3 (mount the skill’s own atlas-id at `<skill>/references/atlas`) is no longer current once skills are routinely global. A successor exists.

**Living thesis:** `autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md` — `.atlas/<encoded-id>/` in the active repo; `references/atlas.md` is activation path only.

Operator 2026-09-03: do not mount anything under `<skill>/references/atlas` moving forward. git-mesh and everything else uses `.atlas`. The only skill-side artefact is the activation path for mount and read/write.
