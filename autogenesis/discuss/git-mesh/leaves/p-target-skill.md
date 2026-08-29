---
type: protostar
title: "Is --target-skill a path override or a different kind of install?"
created: 2026-08-29
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "Installing into references/atlas mutates a skill package. That is not the same as default .atlas."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: derived_from
---

## Growth path

Either `--target` is always a path, and `--target-skill name` is sugar for `<skill>/references/atlas`, or skill-embedded memory is never an install target (only authored in place).

## Open question

May `atlas install` write into a skill package at all?

## Origin

Doubt about `.atlas` vs `--target-skill`.
