---
type: decision
title: "Git is the default overlay; headless Atlas is limited"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Contradiction 6 pinned. Git default. No-git is a documented headless mode. Local git still counts (e.g. Grok Cloud)."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-git-optional.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-capabilities-by-mode.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-optional-git-cut.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

1. **Git is the default and natural way** to work with Atlas. The mounted folder is a git working copy. Publish is commit / push / PR.
2. **Local git counts.** A repo that never leaves the harness (Grok Cloud / Ask with weak remotes) is still the overlay. Overlay ≠ “must have GitHub.”
3. **Headless Atlas** (no git binary / no repo) is allowed for **basic** work only. Capabilities are a strict subset. It is not a second architecture.
4. A **capability-by-mode** page is required and current (`atlas-capabilities-by-mode.md`). Change the matrix when verbs change; do not leave mode behaviour implicit.

## Rationale

Grok Cloud’s limited remote support created the “git optional” sentence. Local git still gives history, branches, and honest writes. Inventing a parallel overlay for that environment splits the product.

## Alternatives considered

- Git required always, fail closed with no reader — rejected; basic local compile/query should live.
- Full peer writer without git — rejected; that reintroduces a second overlay.
- Remote-only git (GitHub or nothing) — rejected; local git is enough to be “on the overlay.”
