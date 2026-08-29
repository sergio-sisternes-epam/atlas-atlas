---
type: experience
title: "2026-08-26 read microsoft/apm auth source"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "GitHub inspection of AuthResolver and GitHubTokenManager, persisted into this fabric."
origin: internal
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: records
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: records
  - path: autogenesis/discuss/git-mesh/apm-env-outranks-gh.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Context

On the atlas-auth branch the user asked to check GitHub for microsoft/apm docs and code, then asked whether that reading had been captured as discussion memory.

## What happened

Repo `microsoft/apm` was read at main SHA `6be370d`. Primary files: `src/apm_cli/core/auth.py`, `src/apm_cli/core/token_manager.py`, `docs/src/content/docs/getting-started/authentication.md`. Findings were written to `apm-auth-precedent.md`. The env-before-gh order was then lifted to `apm-env-outranks-gh.md` so it is a first-class claim, not only chat.

## Outcome

Precedent is queryable in this Atlas. Helper implementation was not started.
