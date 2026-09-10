---
type: experience
title: "Implement shared vs dedicated Atlas store strategy"
created: 2026-09-10
work_id: 2026-09-10-atlas-store-modes
status: closed
description: "Shipped atlas store init/rehost, mesh strategy, GitHub atlas-branch ruleset driver, and path init/migrate cards. Mount stays git submodule."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: autogenesis/plans/2026-09-10-atlas-store-modes.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
---

## Context

Approved Autogenesis design for two storage strategies. Mount remains a git
submodule in both. Init never creates a host repository. CLI `atlas migrate`
stays staging import; strategy moves use `atlas store rehost`.

## What happened

Atlas #20 merged 2026-09-10. Default `atlas store init` is **shared** (consumer
`atlas` branch). **Dedicated** still uses an existing separate store remote.
Mesh `strategy` is required on shared rows (`ref: atlas`); missing field means
dedicated. GitHub driver applies a no-direct-push ruleset after the first
`atlas` push; self-hosted warns and continues.

Path migrate uses `migrate_mode: relocate | strategy`. Review follow-ups
redacted fetch-stderr userinfo and split GHE `:port` (strip for credential
lookup, keep on HTTPS insteadOf).

## Outcome

Consumer repos can host knowledge on `atlas` without a second GitHub
repository. History-preserving rehost works both ways against an existing
destination.

## Changed files (skill)

- `scripts/atlas_cli/commands/storecmd.py` `mount.py`
- `scripts/atlas_cli/core/gitops.py` `github_driver.py` `meshfile.py`
- `scripts/atlas_cli/schemas/atlas-mesh.schema.json`
- `references/paths/init.md` `migrate.md` `mount.md`
- `SKILL.md` `README.md` `CHANGELOG.md`
