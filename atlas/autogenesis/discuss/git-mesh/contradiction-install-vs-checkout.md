---
type: document
title: "Contradiction 3 — atlas install vs atlas checkout"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: current
description: "Two names for materialise. Proposed: install is the verb; checkout is not a second product command."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-install-vs-checkout.md
    kind: related
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The fight

Early design: `atlas checkout <remote-url>` plus `atlas resolve`.
Later design: `atlas install` (APM-like, from config or pointer).

Agents cannot be taught two materialise verbs for the same job.

## Proposed resolution (not pinned)

**`install` is the only materialise verb.**

- `atlas install <pointer>` — pointer is an MD URL, `atlas://`, or host/path id. Translation + `atlas auth` produce the git remote. Default target `.atlas/`. Optional `--target`.
- A skill or mesh list is batch `atlas install` of declared pointers.
- `resolve` stays a **map** (pointer → local path if already installed). It does not clone.
- Drop `checkout` as a user/agent command. Git’s own `checkout` remains a git word inside the working copy.

## Why this fits #2

Install does not need the user to paste a scheme. Auth alias + translation supply transport. The argument that “we must say checkout because we cannot know protocol” is gone.
