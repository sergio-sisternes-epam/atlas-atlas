---
type: document
title: "APM code: env PATs outrank gh — that forks the original sketch"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Claim from microsoft/apm AuthResolver._resolve_token. Copying APM means env-first, not gh-first."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-precedence.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

The original atlas-auth sketch said: default to `gh`, fall back to PAT.

`AuthResolver._resolve_token` in microsoft/apm does the opposite for GitHub-class hosts:

1. per-org `GITHUB_APM_PAT_{ORG}`
2. `GITHUB_APM_PAT` → `GITHUB_TOKEN` → `GH_TOKEN`
3. only then `gh auth token --hostname <host>`
4. then `git credential fill`

If Atlas “replicates APM”, `gh` is not the default. It is the fallback when those env vars are unset.

Choosing gh-first is a deliberate fork and must be recorded as such on `leaves/p-auth-precedence.md`. This page does not pick a side. It pins what the code does.
