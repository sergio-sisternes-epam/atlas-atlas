---
type: decision
title: "The materialise verb is atlas mount"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Contradiction 3 pinned. Mount the Atlas onto the filesystem. Git is the DFS. Atlas is OKF + graph navigation."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-install-vs-checkout.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/verb-materialise-name.md
    kind: records
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-install-vs-checkout.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

The agent-facing materialise verb is **`atlas mount`**.

Mount means: put this Atlas onto the local filesystem so the agent can read and write it. Git is the distributed file-system engine. Atlas provides OKF and graph navigation (`mesh`, `atlas://`, query).

- `atlas mount <pointer>` — pointer via translation + `atlas auth` → working copy on disk → mesh row.
- Default target `.atlas/` unless `--target` is set.
- `atlas resolve` maps pointer → local path if already mounted. It does not mount.
- Do not ship `atlas install` or `atlas checkout` as product verbs.

`mount` here is not a second overlay tree. The mounted folder *is* the git working copy.

## Rationale

Install implies a package manager. Checkout implies a git branch. Mount names the actual effect: a store appears on the filesystem.

## Alternatives considered

- `install` — rejected, APM/npm baggage.
- `checkout` — rejected, git-branch baggage.
- `add` / `attach` / `clone` / `connect` — weaker than mount for “tree now on disk.”

## Consequences

- Contradiction 3 closed.
- Agent verb set now includes `init`, `mount`, `resolve`, `query`, `auth`, plus git to publish.
- Next in queue: **#5 `--target-skill` vs path-as-signal**. Then **#6 git optional vs git is the overlay**.
