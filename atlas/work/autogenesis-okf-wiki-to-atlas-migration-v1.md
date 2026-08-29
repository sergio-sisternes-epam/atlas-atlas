---
type: work
title: "Migrate autogenesis skill process memory from okf-wiki to Atlas"
created: 2026-08-23
work_id: autogenesis-okf-wiki-to-atlas-migration-v1
status: done
description: "Bootstrap dedicated Atlas root under autogenesis skill; migrate authoritative discipline knowledge pages from its okf-wiki store; update autogenesis discipline so only Atlas paths are used for memory (okf-wiki becomes legacy for this skill)."
relates_to:
  - path: work/atlas-agentic-integration-v1.md
    kind: follows
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: decisions/prefer-atlas-over-okf-wiki-interim.md
    kind: related
---

## Scope

1. Create `/home/workdir/.grok/skills/autogenesis/references/atlas/` as the skill's durable process-memory store (SCHEMA + index + log + templates).
2. Migrate key claim-bearing knowledge pages that define Autogenesis memory discipline (especially the "memory via okf-wiki" page and related lineage/vocabulary pages) into the new Atlas, superseding the old authority.
3. Leave bulk historical raw experiences staged or deferred (full live migration remains under `atlas-bm25-and-live-migration-v1`).
4. After content is green, hand off to autogenesis skill for discipline review so that SKILL.md + path modules + workflow-discipline reference **only** Atlas (query/remember/work) and never require okf-wiki activation for memory ops.

## Status

implementing — hub opened; bootstrap + selective migrate next.

## Outcomes

- New Atlas root exists and compiles green.
- Authoritative memory pages live under the new root with `relates_to` edges.
- Autogenesis discipline updated (separate run under autogenesis skill).
- This work closes when compile green + discipline review complete.

## Related

See frontmatter `relates_to` (authoritative).
