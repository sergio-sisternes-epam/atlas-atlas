---
type: document
title: "Counter — JSON Schema has no Buf-class breaking checker"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Tightening overlay constraints breaks existing pages. JSON Schema compatibility checkers are immature. Plan deferred semver."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: counters
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
---

## Content

Protobuf/Buf can `buf breaking` and reject incompatible schema pushes. JSON Schema does not have an equivalent mature checker. Making an optional field required, or tightening `maxLength`, is a breaking change for existing instances.

The plan fail-closes on *key clashes*, not on tightening `templates.by_type` required lists. A newer overlay can add required frontmatter keys; compile then fails every old page. That is a silent break of stores, not a merge clash.

Sources: [Buf breaking](https://buf.build/docs/breaking/); [Confluent schema evolution](https://docs.confluent.io/platform/current/schema-registry/fundamentals/schema-evolution.html); [GSoC JSON Schema compatibility checker](https://github.com/json-schema-org/community/issues/984).

Severity: high. Plan residual “no overlay semver” is the hole.

**Pin (autonomous, operator away 2026-09-03):** no Buf-class checker in this work. Because overlays cannot mutate core types (counter 1), tightening core contracts is out. Replacing an installed overlay that changes that overlay’s own required keys is compile-critical unless `--force`. Full compatibility matrix stays out of scope.

## Provenance

think-challenge 2026-09-03 before sign-off.
