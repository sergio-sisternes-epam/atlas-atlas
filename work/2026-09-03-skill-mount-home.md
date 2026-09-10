---
type: work
title: "Skill Atlas write-home is the active git repo (.atlas submodule)"
created: "2026-09-03"
work_id: "2026-09-03-skill-mount-home"
status: implementing
description: "Stop skill-internal references/atlas store. Mount dedicated Atlases as parent-repo submodules under .atlas/<id>/."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: related
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: follows
  - path: experiences/2026-09-03-implement-skill-mount-home.md
    kind: related
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
  - path: decisions/consuming-skill-atlas-activation-card.md
    kind: related
  - path: decisions/unmounted-atlas-uri-non-blocking.md
    kind: related
---

## Scope

Atlas skill 0.8.5: paths `mount`, `init`, and `migrate`; default mount is a git submodule at `.atlas/<encoded-id>/`; no store under the skill package. Other skills (discuss, autogenesis) still name `--target references/atlas` until they migrate.

## Status

Atlas package implement landed. Autogenesis consult (session Atlas mount impact) mapped leftover pins: own-store hardening is one Run after Atlas 0.8.5 is loaded; other-subject G2 and migrate-init deferred. Autogenesis-atlas persist from that session failed (empty gitlink, `.atlas/` gitignored).

## Outcomes

- Path `mount`: card carries `atlas_id` and `ref`; generic for any session.
- Path `init`: requires existing `remote`; never creates the host repo.
- Path `migrate`: moves one skill's own store from `references/atlas`; other
  subjects migrate independently.
- `atlas mount` refuses without a parent git repo; in-parent default is submodule, not a gitignored clone.
- Consuming-skill declaration is pinned as an exact five-field Atlas mount card
  in the main `SKILL.md`; no copied module or local registry row.
- Unmounted external `atlas://` dependencies remain visible warnings but do not
  fail compile; local actionable warnings and critical issues retain exit 1/2.

## Remaining before done

- Add idempotent card stamping and visible failure semantics to
  `references/paths/init.md` and `references/paths/migrate.md`.
- Run the relevant construct scenario after the product guidance is complete.
- Migrate Autogenesis separately after Atlas 0.8.5 is the loaded skill.
