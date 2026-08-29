---
type: decision
title: "Interim: prefer Atlas over okf-wiki for process memory"
created: 2026-08-23
status: accepted
work_id: atlas-agentic-integration-v1
description: "Temporary: use Atlas skill paths for remember/query/work until migration; okf remains format authority; okf-wiki deferred for new memory."
relates_to:
  - path: work/atlas-agentic-integration-v1.md
    kind: implements
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: experiences/2026-08-23-agentic-integration-implement.md
    kind: records
---

## Decision

Until okf-wiki content is migrated into Atlas, agents **should use the Atlas skill** (`query` / `remember` / `work` paths) for process memory and knowledge capture on Atlas-related work — **not** okf-wiki ingest/query discipline.

## Rationale

Atlas is the operational successor. Path modules encode the intended agent behaviour. Dual-writing to okf-wiki would split the graph and prolong migration debt.

## Alternatives considered

- Continue dual-home to okf-wiki and Atlas — rejected (duplicate effort, drift).
- Disable okf-wiki skill entirely — rejected (legacy stores and migration still need it later).

## Consequences

- New experiences/decisions for Atlas work → `references/atlas/` via **remember**.
- Format-only questions → skill **okf** (unchanged).
- Full corpus migration remains draft work `atlas-bm25-and-live-migration-v1`.
- This decision is **interim** and should be superseded when migration completes.
