---
type: decision
title: "MVP agent verbs — init auth mount resolve query compile; git for history"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Six Atlas commands. Git in the resolved mount root for update and publish. No install/checkout/sync."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/agent-verbs.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

Agent-facing Atlas surface in MVP:

- `init` — create a local Atlas in a folder
- `auth login|list|logout` — host alias
- `mount <pointer>` — first materialise; submodule if parent is git; refuse dirty/wrong-branch
- `resolve <pointer>` — id → mount root; page URI → file
- `query` — search visible trees; no auto-mount
- `compile` — validate; warn on unknown `atlas://`

Git in `resolve <id>`: fetch, pull, checkout, commit, push, PR.

Not Atlas verbs: `install`, `checkout`, `sync`, `--target-skill`.

Headless: `compile`, `query`, edit-in-place only.
---
