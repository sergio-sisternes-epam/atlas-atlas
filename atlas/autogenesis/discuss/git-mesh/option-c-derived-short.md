---
type: document
title: "Option C — derived short form is primary"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: current
description: "Primary id is a scheme-free short form (host/path). User lean after protocol-is-not-identity. Still forming, not pinned."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: related
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Primary id is a deterministic short form derived from the repository URL, for example `github.com/org/my-atlas` or a stable hash. Everyday `atlas://` references use that form. No separate alias table is required if the derivation is total.

Still unique, shorter than a full URL with scheme. Needs a locked normalisation function (scheme strip, `.git` suffix, case, monorepo path).
