---
type: document
title: "Branch — atlas auth helper (APM-like transport)"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "New discussion branch. Identity stays scheme-free; this branch owns how Atlas talks to git remotes."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: related
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: backed_by
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Opened as its own branch because auth/transport is a large design chunk and must not be smuggled into the identity pin.

User sketch:

- Replicate the microsoft/apm authentication mechanism rather than inventing a third chain.
- Default: `gh` (already signed-in CLI). **Challenged** by APM source: env PATs outrank `gh`. See `apm-env-outranks-gh.md`.
- Fall back: PAT via environment variables.
- Support SSH (keys already available to the agent / ssh-agent).
- An `atlas auth` helper configures the environment (and protocol) so mount operations can run non-interactively.

Identity input to the helper is the short host/path id, not a full URL. After reading microsoft/apm source, the closest object is `AuthResolver`: `(host, org)` in, `AuthContext` + `git_env` out. Token-bearing traffic is HTTPS; SSH is a separate transport using the machine agent.

This branch is discussion only. No helper class is being written from this page.

## Current reality vs alternative

Current: auth is a separate branch from tension 1.
Alternative not taken: bake protocol into `atlas://` or into mesh `id`.
