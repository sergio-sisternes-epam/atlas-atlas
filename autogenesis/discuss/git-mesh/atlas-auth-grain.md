---
type: document
title: "Orbit — atlas auth alias grain"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "What an atlas auth alias keys on: host, org, or repo. Translation uses that key."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: backed_by
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-precedence.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-protocol-choice.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-helper-surface.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## What is already pinned

Pointer ≠ credential. `atlas auth` stores an alias. Translation: pointer → alias → git remote. Atlas-id scheme-free.

## This orbit

What is the **key** of the alias?

| Grain | Example key | Fits | Cost |
|-------|-------------|------|------|
| Host | `github.com` | one login per server | cannot isolate orgs |
| Host + org | `github.com/acme` | matches APM PAT-per-org | more aliases to manage |
| Repo | `github.com/acme/atlas` | max isolation | alias explosion |

## Proposed lean (not pinned)

Default alias is **host**. Optional **org** override when a second identity is needed on the same host. No per-repo alias in MVP.

Translation: parse pointer → `host` + `org` → most specific matching alias → transport (https+token or ssh) stored on that alias.

Commands (sketch only):

```text
atlas auth login [--host github.com] [--org acme] [--ssh]
atlas auth list
atlas auth logout [--host …] [--org …]
```

`atlas mount` never prompts if a matching alias exists; otherwise it fails and tells the agent to `atlas auth login`.

Precedence inside one alias (still forming): env PAT vs `gh` vs stored token — APM says env wins; user once preferred `gh` first. Not this pin.
