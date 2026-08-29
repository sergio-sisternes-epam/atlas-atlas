---
type: decision
title: "atlas auth — host grain, backends, gh preferred + PAT fallback"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Alias key host + optional org. Backends gh|token|ssh|git-credential. GitHub: gh preferred, PAT first-class."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-auth-grain.md
    kind: records
  - path: autogenesis/discuss/git-mesh/atlas-auth-backends.md
    kind: records
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: backed_by
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

1. Alias key: **host**, optional **org** override. No per-repo alias in MVP.
2. Backends: `gh` | `token` | `ssh` | `git-credential`.
3. GitHub-family (`github.com`, `*.ghe.com`, GHES with `gh --hostname`): **`gh` preferred**, **PAT (`token`) first-class fallback** when `gh` cannot hold the right account, is missing, or the user passes a token. SSH remains valid.
4. Any other host, including self-hosted: `token` or `ssh` (or `git-credential`). Never assume `gh`.
5. Atlas shells out to `gh`; it does not vendor it. Tokens never appear in Markdown.

`atlas mount` uses translation: pointer → most specific alias → backend → remote. No alias → fail, tell the agent to `atlas auth login`.

## Alternatives considered

- `gh`-only on GitHub — rejected (second enterprise/org, CI).
- Per-repo aliases in MVP — rejected.
- Forge-specific CLIs (`glab`, …) in MVP — deferred; add as named backends later.
---
