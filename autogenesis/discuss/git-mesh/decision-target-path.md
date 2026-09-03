---
type: decision
title: "Default mount is .atlas/; references/atlas stays skill-internal"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: superseded
reality: archive
description: "Superseded 2026-09-03. Clause 3 (skill-internal references/atlas store) is dead. Successor: decision-mount-dot-atlas-only.md."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-target-skill.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-target-skill.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/skill-mount-home/exit-skill-internal-store.md
    kind: kva_supersede
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: contradicts
---

## Decision

1. Default `atlas mount` target is **`.atlas/<encoded-id>/`**.
2. The only override is **`--target <path>`**. There is no `--target-skill`.
3. `<skill>/references/atlas` is that skill’s **internal memory** (one authored root). Mount *that skill’s own* atlas-id there only when explicit.
4. Other corpora the skill uses are mesh members under `.atlas/` (or another `--target`), not extra trees under `references/`.
5. Other skills may write **pages** into a skill Atlas they have mounted. That does not license stacking N roots in one folder.

## Rationale

The path is a signal. Sugar that writes foreign trees into process memory destroys it.

## Alternatives considered

- `--target-skill foo` → `foo/references/atlas` — rejected.
- `references/atlases/<id>/` inside the skill — rejected; vendors others’ graphs into the skill package.

## Consequences

Contradiction 5 closed. Next: **#6 git optional vs git is the overlay**.
