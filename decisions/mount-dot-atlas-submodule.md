---
type: decision
title: "Dedicated store mounts at .atlas/<id>/ as a parent git submodule"
created: "2026-09-03"
status: settled
work_id: "2026-09-03-skill-mount-home"
kva: alive
description: "Supersedes package-shapes mount-at-references/atlas. Skill package has path mount, not a store."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: decisions/package-shapes.md
    kind: supersedes
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: follows
  - path: decisions/consuming-skill-atlas-activation-card.md
    kind: related
  - path: decisions/unmounted-atlas-uri-non-blocking.md
    kind: related
---

## Decision

1. Two package shapes remain: embedded vs dedicated. Dedicated OKF root is still git root.
2. This skill’s canonical store stays dedicated (`github.com/sergio-sisternes-epam/atlas-atlas`).
3. The mount is **`<git-root>/.atlas/<encoded-id>/` as a git submodule of the active repository**. Compile/query `--root` is that path.
4. The skill package does not contain a store. Path `mount` (card `atlas_id`, `ref`) mount-if-missing, then other Atlas paths. Path `init` scaffolds only after an existing git remote is given.
5. No git parent: refuse mount and persist.
6. A consuming skill names its store in the main `SKILL.md`; the exact card
   contract is `decisions/consuming-skill-atlas-activation-card.md`.

## Rationale

A global skill install made `<skill>/references/atlas` an untracked write-home. Path-as-signal does not survive that. Git remains the overlay; the parent gitlink is how a session PR pins the store SHA.

## Alternatives considered

- Keep `--target references/atlas` for this skill’s memory — rejected.
- Gitignored clone under `.atlas/` — rejected; must be a submodule.
- Auto-create host repositories on init — rejected.

## Consequences

Agents resolve `--root` via `atlas resolve <atlas_id>`. Store commits are PRs on atlas-atlas (or the named store). Parent PRs only bump the gitlink. Other skills load path `mount` with their own `atlas_id`.

`init` starts from an existing remote and never creates a host repository.
`migrate` moves one skill's own store per Run. Both stamp the consuming
skill's mount card; other subject skills migrate independently.
