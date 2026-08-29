---
type: protostar
title: "atlas install vs atlas checkout — one verb or two?"
created: 2026-08-28
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "New design names install (APM-like). Earlier design named checkout + resolve."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: related

---

## Growth path

Either rename checkout → install and keep resolve as the map, or treat install as “batch checkout from skill/APM config” and keep checkout as the one-URL verb.

## Open question

Does `atlas install` read a manifest (skill / apm.yml / mesh fragment) while `atlas checkout <url>` stays the manual one-shot?

## Origin

T2 plus atlas-as-own-repo.
