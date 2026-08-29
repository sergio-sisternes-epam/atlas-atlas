---
type: protostar
title: "Monorepo or multirepo for Atlas packages?"
created: 2026-08-28
status: superseded
kva: forming
reality: current
growth: true
star_kind: tension
description: "User left both open. Decides install target, subpath, and APM package grain."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-monorepo-id.md
    kind: related

---

## Growth path

Multirepo: one git repo = one Atlas = one APM package. Simplest id and install.
Monorepo: one git repo, several Atlas roots (subpaths). Needs the parked T1 subpath rule.

## Open question

Is the default grain “one Atlas per APM package”, with monorepo as an allowed exception?

## Origin

atlas-as-own-repo design.
