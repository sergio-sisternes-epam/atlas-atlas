---
type: protostar
title: "What is the atlas auth helper surface?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: refine
description: "User asked for a helper class that configures env vars. Shape only; no implement."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: derived_from
---

## Growth path

Sketch inputs (short atlas-id, desired access read|write, host) and outputs (clone URL, env dict, maybe GIT_SSH_COMMAND). Keep it a discussion sketch.

## Open question

CLI verb (`atlas auth env --id …`) plus a library used by mount, or env-only with no extra CLI?

## Origin

atlas-auth branch.
