---
type: document
title: "Discussion hub — Embedded atlas branch vs Dedicated store repo"
created: "2026-09-10"
status: in-discussion
kva: alive
reality: current
description: "discussion_root. Subject and objective locked. Does not move."
origin: user
sensitivity: internal
stage: discussion
artifact: work/2026-09-10-atlas-store-modes.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: related
  - path: atlas-project/branching-model.md
    kind: related
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: related
  - path: work/2026-09-03-skill-mount-home.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-identity.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-naming-two-axes.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-name-collision.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-default-shared.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-default-embedded.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-github-driver.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-self-hosted-protection.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-self-hosted-warn.md
    kind: follows
  - path: autogenesis/discuss/store-modes/setup-path-orbit.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-setup-path.md
    kind: related
  - path: autogenesis/discuss/store-modes/p-migrate-path.md
    kind: related
  - path: autogenesis/discuss/store-modes/migrate-path-orbit.md
    kind: follows
---

## Content

Subject: how an Atlas store is hosted relative to the consumer repository.

Objective: enable two store modes, both mounted as git submodules, with a setup path (default Embedded) and a migrate path between modes.

This page is `discussion_root`. It does not move.

### Operator proposal (2026-09-10)

1. Embedded: Atlas creates an `atlas` branch in the consumer repository. Knowledge lives on that branch. A GitHub driver offers branching setup and protection. Self-hosted git gets fallback instructions.
2. Dedicated: keep the current separate-repository store.
3. Mounting stays git submodule in both modes.
4. Offer an activation path to set the mode. Default is Embedded.
5. Offer an activation path to migrate between modes.

### Current reality this orbit must not silently rewrite

Alive decision `decisions/mount-dot-atlas-submodule.md`: dedicated stores mount at `.atlas/<id>/` as a parent git submodule. This skill's own store is dedicated.

Alive git-mesh pin `autogenesis/discuss/git-mesh/decision-package-shape-mvp.md`: "Embedded" there means the git unit is the skill or project repo and the store `subpath` is `references/atlas`. That is not an `atlas` branch.

Alive vision note `atlas-project/branching-model.md`: knowledge grows on git branches; contribution still materialises a submodule.

The live distinction is therefore naming plus identity. The operator's Embedded is a same-repo `atlas` branch with a submodule checkout. The settled Embedded is a subpath inside the product tree. Those two must not share one word without a pin.

### Batch on the hub

1. Store identity — engaged: pin-identity-consumer-repo.md (shared uses consumer repo, `ref: atlas`).
2. Naming — engaged: pin-naming-two-axes.md (Embedded stays `references/atlas`; storage strategy is dedicated vs shared).
3. GitHub driver — engaged: pin-git-common-github-adds.md. Self-hosted floor — engaged: pin-self-hosted-warn.md (warn and continue).
4. Default — engaged: pin-default-shared.md (new consumers shared; existing dedicated stays until migrate).

### Set aside

Git-mesh mount-lifecycle, checkout-resolve, and skill-mount-home remain settled for Dedicated. This orbit does not reopen whether mount is a submodule.
