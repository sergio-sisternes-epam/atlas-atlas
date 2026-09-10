---
type: document
title: "Pin — self-hosted shared warns and continues"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Non-GitHub remotes still run the common git process. Missing branch protection is documented and warned, not a hard fail."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/p-self-hosted-protection.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-git-common-github-adds.md
    kind: follows
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: on a non-GitHub remote, shared setup **warns and continues**.

Atlas still runs the common git process (branch `atlas`, same-repo submodule). It documents that the mandatory GitHub ruleset (no direct push to `atlas`) is absent. It does not fail closed. It does not require an attestation.

GitHub-hosted shared still applies that ruleset as mandatory.

## Provenance

Operator choice on the self-hosted protection tension.
