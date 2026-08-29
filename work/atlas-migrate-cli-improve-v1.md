---
type: work
title: "Improve Atlas migrate CLI and skill guidance"
created: 2026-08-23
work_id: atlas-migrate-cli-improve-v1
status: designed
description: "From live autogenesis wiki→Atlas migration pain: improve migrate/promote UX, bulk workflows, skill path docs, and agent guidance so full-store migrations are less error-prone."
relates_to:
  - path: experiences/2026-08-23-design-plan-atlas-migrate-cli-improve-v1.md
    kind: related
  - path: work/autogenesis-okf-wiki-to-atlas-migration-v1.md
    kind: follows
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: related
  - path: decisions/prefer-atlas-over-okf-wiki-interim.md
    kind: related
---

## Scope

Improve the **atlas migrate / promote CLI** and the **atlas skill** (SKILL.md + remember path) based on problems observed during the full autogenesis okf-wiki → Atlas migration.

In scope:
- CLI: bulk inventory, dry-run, progress, clearer next-step messaging, optional carry-body on promote
- Skill docs: explicit full-directory vs selective guidance; staging emptiness contract; agent checklist for claim mesh
- Optional: batch promote helper, staging summary command

Out of scope (separate work):
- Full BM25 index (`atlas-bm25-and-live-migration-v1`)
- Automatic claim synthesis without agent review

## Status

**draft** — work idea opened from autogenesis design run after migration retrospect.

## Plan

- **Atlas-local (authoritative):** `experiences/2026-08-23-design-plan-atlas-migrate-cli-improve-v1.md`
- Provenance copy: `artifacts/autogenesis-plans/2026-08-23-atlas-migrate-cli-improve-v1.md`

## Outcomes (target)

1. Agent can migrate a whole legacy wiki with fewer false starts.
2. Promote either scaffolds (current) or optionally preserves source body.
3. Skill remember path documents the bulk path and the “staging must be 0” hard rule with examples from this migration.
4. Design plan approved → implement in a follow-on Run.

## Related

See frontmatter `relates_to`.
