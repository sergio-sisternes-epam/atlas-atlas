---
type: protostar
title: "How is a git URL normalised into an atlas-id?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Scheme, .git suffix, case, and host aliases must be decided before URL-primary identity works."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: derived_from
---

## Growth path

Settle whether the canonical id includes `https://`, strips `.git`, lowercases the host, and treats `github.com/org/repo` as equal to the SSH form.

## Open question

Full URL including scheme, or a normalised host/path form?

## Origin

Tension 1 — URL-as-id ergonomics.
