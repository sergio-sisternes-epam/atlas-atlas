---
type: document
title: "Pin — git process is common; GitHub driver adds protection"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "Shared setup is git everywhere. GitHub driver adds rulesets. Direct push to atlas is mandatory-blocked on GitHub. Copilot Reviews on PRs are recommended."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/hub.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-default-shared.md
    kind: follows
  - path: autogenesis/discuss/store-modes/p-github-driver.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10:

The **git process is common** for every host: create or reuse branch `atlas`, register the same-repo submodule, and use ordinary commits and pull requests into that branch.

The **GitHub driver adds** GitHub-specific rules on top of that process. It does not replace git.

Mandatory on GitHub: a ruleset that prevents direct push to `atlas`.

Recommended on GitHub: Copilot Reviews on every pull request into `atlas`.

Self-hosted git still runs the common process. It does not get GitHub rulesets. Whether Atlas fails closed there, or only documents the missing protection, is not pinned.

## Provenance

Operator reply on the GitHub-driver batch item.
