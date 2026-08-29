---
type: decision
title: "Atlas and APM stay uncoupled products"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "No product integration. Agents learn Atlas CLI + git. APM must not grow Atlas hooks."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-apm-git-trace.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Decision

Atlas and APM are different open-source products. Do not couple them (no Atlas plugin inside APM, no APM-specific restore hook required for Atlas to work).

Agents in a session must know Atlas as its own tool: `init`, `install`, `query` (and the rest of the verb surface), plus how to submit new memories through **git** (commit / push / PR).

APM may still *distribute* packages that happen to contain an Atlas tree. That is file layout, not a product contract.

## Rationale

Hooking materialise so APM “understands” Atlas would make two independent projects one system. The successful loop today is agent + git + Atlas store. Keep that.

## Alternatives considered

- APM preserves or re-links `references/atlas` as a submodule on install — rejected as product coupling.
- Atlas install is a hidden step inside `apm install` — rejected for the same reason.

## Consequences

- `p-apm-git-trace` is no longer “teach APM.” It becomes: after any install (APM or otherwise), the **agent runs Atlas commands** to init/install/query and uses git to publish.
- Mesh composition via APM *package dependencies* stays a possible *user* workflow, not an Atlas↔APM API.
