---
type: document
title: "Pin — skill references/atlas is a pointer, not the store"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "Skill path points at the repo-owned mount and instructs mount-if-missing. Path-as-signal is retired for this orbit."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-both-write-homes.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: counters
  - path: autogenesis/discuss/skill-mount-home/global-skill-out-of-repo.md
    kind: related
---

## Content

Operator pinned: the skill’s `references/atlas` becomes a **pointer plus mount-if-missing**, not the write-home. Path-as-signal is accepted as dead on this orbit.

Rejected here:

- Submodule or symlink under the skill path that still looks like internal memory.
- Dropping the skill path entirely so skills only name an atlas-id.

The pointer’s concrete form (file, stub directory, mesh entry, SKILL.md instruction) is not pinned yet. Neither is the target layout (`.atlas` as a file versus `.atlas/<encoded-id>/`).

### Outcome

KVA alive. Git-mesh skill-internal exception is in play. Next fail-fast: no active git repository, then the `.atlas` shape.
