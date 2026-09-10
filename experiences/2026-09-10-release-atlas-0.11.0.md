---
type: experience
title: "Release Atlas 0.11.0 and pin the marketplace catalog"
created: 2026-09-10
work_id: 2026-09-10-atlas-store-modes
status: closed
description: "Tagged v0.11.0 on main SHA 1c5a415 after changelog PR and Atlas CI pre_tag_decision=ready to tag; catalog pin atlas 0.11.0 in sergio-sisternes-epam/apm-marketplace."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: experiences/2026-09-10-implement-atlas-store-modes.md
    kind: follows
---

## Context

Store-modes implementation was already on Atlas `main` (PR 20) with the
atlas-atlas gitlink (PR 21). Version surfaces already read 0.11.0. CHANGELOG
still listed store-modes and SMR under Unreleased; marketplace still pinned
atlas 0.10.0.

## What happened

Changelog PR 22 promoted Unreleased store-modes notes to `## 0.11.0 - 2026-09-10`
and recorded `## 0.10.0 - 2026-09-09` for the already-tagged SMR release.
Merged SHA `1c5a4158d5ff091bc2de78d6303cddf7e9bb4418`. Atlas CI on that `main`
push recorded `pre_tag_decision=ready to tag`. Annotated tag `v0.11.0` and
GitHub Release followed. Marketplace PR 11 ran `apm pack` (apm-cli 0.30.0)
and pinned `atlas` version 0.11.0 at that commit; merge published the catalog.

Do not `apm pack` the Atlas package itself. Catalog `ref` is the immutable
commit SHA, not a mutable branch.

## Outcome

Consumers install `atlas@sergio-sisternes-epam` at 0.11.0 (shared vs dedicated
store hosting). Provenance: release
https://github.com/sergio-sisternes-epam/atlas/releases/tag/v0.11.0
