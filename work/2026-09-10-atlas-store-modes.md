---
type: work
title: "Two Atlas store modes — shared branch and dedicated repo"
created: "2026-09-10"
work_id: "2026-09-10-atlas-store-modes"
status: done
description: "Shipped shared (atlas branch on the consumer repo) vs dedicated (separate store repo). Init default shared; rehost preserves history. Mount stays git submodule."
origin: user
sensitivity: internal
stage: implement
artifact: autogenesis/discuss/store-modes/hub.md
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: related
  - path: autogenesis/plans/2026-09-10-atlas-store-modes.md
    kind: related
  - path: experiences/2026-09-10-implement-atlas-store-modes.md
    kind: records
  - path: experiences/2026-09-10-release-atlas-0.11.0.md
    kind: records
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-naming-two-axes.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-default-shared.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-self-hosted-protection.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-self-hosted-warn.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-setup-extend-init.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-mesh-strategy-field.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-shared-bootstrap.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-existing-atlas-branch.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-existing-atlas-branch.md
    kind: related
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: related
  - path: autogenesis/discuss/store-modes/migrate-path-orbit.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-migrate-one-path.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-migrate-preserve-history.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-migrate-both-directions.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-migrate-github-driver.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-identity.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-name-collision.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-github-driver.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-default-embedded.md
    kind: related
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: related
  - path: atlas-project/branching-model.md
    kind: related
  - path: work/2026-09-03-skill-mount-home.md
    kind: related
---

## Scope

Shape two first-class store modes for Atlas:

- Embedded: knowledge lives on an `atlas` branch of the consumer repository. Mount is still a git submodule. GitHub gets a driver for branch setup and protection. Self-hosted git gets fallback instructions.
- Dedicated: today's separate store repository. Mount is still a git submodule.

Offer an activation path to set the mode (default Embedded) and an activation path to migrate between modes.

Implement shipped on Atlas #20 (merged 2026-09-10). Mount stays git submodule for both strategies.

## Status

Opened 2026-09-10. Discussion pins recorded. Design implemented. Closed after Atlas #20 merged.

## Outcomes

Shared vs dedicated storage strategy is live: `atlas store init` / `store rehost`, mesh `strategy`, GitHub `atlas` ruleset driver, path init default shared, path migrate `migrate_mode`. CLI `atlas migrate` remains staging import. Released as Atlas **v0.11.0** (`1c5a415`) and pinned in `sergio-sisternes-epam/apm-marketplace`.
