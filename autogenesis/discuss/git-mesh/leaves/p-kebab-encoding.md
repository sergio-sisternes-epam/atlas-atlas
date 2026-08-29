---
type: protostar
title: "What string is kebab-cased into .atlas/<name>?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Need a reversible, collision-free encoding. Scheme-free id vs full checkout URL."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: related
---

## Growth path

Decide the input to kebab-case: `github.com/Org/Repo`, lowercase-all, or the literal checkout URL including scheme.

## Open question

Do two checkouts of the same id via https and ssh share one folder, or is that forbidden because checkout URL is unique?

## Origin

User: `.atlas/<atlas-repo-url-kebab-case>`.
