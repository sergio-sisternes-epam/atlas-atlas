---
type: document
title: "Question — how a consuming skill names Atlas without a store tree"
created: "2026-09-03"
status: in-discussion
kva: alive
reality: current
description: "Operator: init (or migrate) should leave an activation path in the consuming skill so agents know atlas_id. Not a store."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-atlas-md.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/pin-activation-covers-write.md
    kind: related
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
---

## Content

Operator: a skill that uses Atlas must still **reference** it after we forbid `<skill>/references/atlas` as a store. Candidate: path **init** (and likely **migrate**) should (1) ensure the mount exists, (2) mount it, (3) leave an activation path on the consuming skill’s **SKILL.md**.

Set aside: Autogenesis consult recommended skip `references/atlas.md`. That was a file-pointer, not a SKILL Enter card. Reopening the *consumer instruction* without reopening a writeable tree.

Live distinction: atlas_id lives only on Atlas skill’s mount card (agent must already know the id) versus every consuming skill ships an Enter card that names `atlas_id` and loads Atlas path `mount`.

### Batch (not yet 1-by-1)

1. Pin: consuming skill SKILL.md must name `atlas_id` and load Atlas path `mount` (instruction, not a store).
2. Path **init** also stamps that Enter card into the consuming SKILL.md.
3. Path **migrate** does the same for existing skills.
4. Counter — mesh/`atlas-mesh.json` in the session repo is enough; skill package stays silent.
5. Counter — stamping SKILL.md from init is product write and too much magic; humans/agents edit SKILL by hand during migrate.

### Outcome

KVA alive. Current branch until we take the batch.
