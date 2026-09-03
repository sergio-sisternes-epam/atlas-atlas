---
type: experience
title: "2026-09-03 implement skill write-home: .atlas submodule and path mount"
created: "2026-09-03"
work_id: "2026-09-03-skill-mount-home"
status: raw
description: "Discuss pins then Atlas 0.8.5: activation paths mount/init, skill-package store removed, parent gitlink at .atlas/<id>/."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: autogenesis/discuss/skill-mount-home/current-reality.md
    kind: records
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: follows
  - path: decisions/package-shapes.md
    kind: related
  - path: decisions/consuming-skill-atlas-activation-card.md
    kind: related
  - path: decisions/unmounted-atlas-uri-non-blocking.md
    kind: related
---

## Context

Operator concern: globally installed skills write Atlas pages outside the session repo. Discuss orbit skill-mount-home pinned write-home as the active git repository, pointer as path not a tree, no-git refuse, layout `.atlas/<encoded-id>/` as submodule.

## What happened

Atlas skill 0.8.6:

- Removed submodule `references/atlas` from the skill package.
- Added path `mount` (`references/paths/mount.md`): generic; `atlas_id` and `ref` on the Enter card. Atlas passes `github.com/sergio-sisternes-epam/atlas-atlas` / `main`.
- Added path `init` for a new Atlas: ask for existing `remote`; never create the host repository.
- Added path `migrate` for one consuming skill's own store: remove the old
  `references/atlas` gitlink, mount at `.atlas/<atlas_id>/`, and retarget
  roots and checks.
- `atlas mount` refuses without a git parent; default target is a **git submodule** under `.atlas/<id>/`. `.atlas/` is not gitignored.
- SKILL.md tells other skills to load this skill’s `mount` path with their own `atlas_id`, not copy a store tree.
- Compile preserves unmounted external `atlas://` references as visible,
  non-blocking warnings. It exits 0 when they are the only issues.

This session’s atlas-atlas checkout is `.atlas/github.com/sergio-sisternes-epam/atlas-atlas` (gitlink). Discussion fabric was copied here from the old skill submodule before that gitlink was deleted.

## Decisions consolidated

- The active repository is the only write-home. A global skill package is
  never a fallback.
- Dedicated stores are parent-repository submodules under
  `.atlas/<atlas_id>/`; a gitignored clone is insufficient.
- No active git repository means refuse mount and persist.
- `init` requires an existing remote and never creates one.
- A consuming skill's durable reference is the exact five-field mount card in
  its main `SKILL.md`. `init` and `migrate` stamp it idempotently. There is no
  copied module, extra consuming-skill registry row, or
  `references/atlas.md` pointer.
- External Atlas availability is not local store integrity:
  `atlas_uri_unmounted` is informational and exits 0, while actionable local
  warnings still exit 1 and critical issues exit 2.

## Probes

- Mount and resolve use
  `.atlas/github.com/sergio-sisternes-epam/atlas-atlas`.
- Mount outside a git repository exits non-zero without cloning.
- A file pointer is not accepted as an Atlas root.
- Registering the pre-existing `.atlas` checkout required staging its gitlink
  before `git submodule absorbgitdirs`.

## Changed files

- `.atlas/github.com/sergio-sisternes-epam/atlas-atlas` (registered parent gitlink)
- `.gitignore`
- `.gitmodules`
- `README.md`
- `SKILL.md`
- `apm.yml`
- `atlas-mesh.json`
- `references/README.md`
- `references/atlas` (removed gitlink)
- `references/paths/init.md` (created)
- `references/paths/migrate.md` (created)
- `references/paths/mount.md` (created)
- `references/paths/query.md`
- `references/paths/remember.md`
- `references/scenarios/storage-mesh-mvp-adversarial-v1.yaml`
- `references/scenarios/storage-mesh-mvp-adversarial-v2.yaml` (created)
- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/mount.py`
- `scripts/atlas_cli/commands/validate.py`
- `scripts/atlas_cli/core/gitops.py`

## Outcome

Atlas package 0.8.6 implements the active-repository mount and the three generic
activation paths. The exact consuming-skill card is now settled in memory but
is not yet an explicit stamping step in `init.md` and `migrate.md`.

Discuss and Autogenesis still instruct `--target references/atlas`.
Autogenesis's own-store migration and all other consuming-skill migrations
remain separate Runs.

Construct evaluation deferred: `storage-mesh-mvp-adversarial-v2` carries the
no-git refusal, parent-submodule, and non-blocking external-reference
expectations, but no construct Run was completed in this pass.
