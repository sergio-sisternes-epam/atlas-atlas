---
type: protostar
title: "How does the helper choose HTTPS vs SSH?"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: forming
reality: current
growth: true
star_kind: question
description: "APM has APM_GIT_PROTOCOL. Atlas needs an equivalent that never leaks into atlas-id."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: related
---

## Growth path

Protocol is environment preference. Spell the order: explicit flag / env, then existing git config, then default (https vs ssh).

## Open question

Default to HTTPS + `gh`/PAT, and use SSH only when keys are already loaded?

## Origin

atlas-auth branch plus protocol-is-not-identity.
