---
type: decision
title: "Migrate CLI lessons from autogenesis full-store migration"
created: 2026-08-23
status: accepted
work_id: atlas-migrate-cli-improve-v1
description: "Pinned lessons: directory migrate is the bulk path; promote is scaffold-only; staging must reach 0; agent owns claims and relates_to mesh; improvement work is draft under atlas-migrate-cli-improve-v1."
relates_to:
  - path: work/atlas-migrate-cli-improve-v1.md
    kind: implements
  - path: experiences/2026-08-23-autogenesis-migration-problems-and-fixes.md
    kind: records
  - path: work/autogenesis-okf-wiki-to-atlas-migration-v1.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase4.md
    kind: related
---

## Decision

Until `atlas-migrate-cli-improve-v1` ships, agents and docs must treat the following as binding lessons from the live autogenesis migration:

1. **Directory form is the bulk path** — `atlas migrate <legacy-dir> --root <atlas>` is correct for whole-store intake; single-file migrate alone is not “content migrated.”
2. **Promote is scaffold-only** — original body is not copied; agent must complete claims from source/staging before clearing staging.
3. **Staging must be empty for green compile** — never claim memory stored while staging is non-empty.
4. **Agent owns claim mesh** — every page needs type-correct frontmatter, required sections, and `relates_to` that resolve inside the root.
5. **Deferral is explicit** — if bulk historical pages are not claim-rewritten, record a decision and still clear staging (or finish claims). Leaving staging full is not a valid deferral.
6. **Improve the CLI** — inventory summary, dry-run, optional body-carry on promote, skip-existing, and batch helpers are product work under `atlas-migrate-cli-improve-v1`, not excuses to skip the above.

## Rationale

Observed failure modes (selective-only, thin scaffolds, non-empty staging, broken edges) all map to gaps between CLI behaviour and agent expectations. Pinning lessons prevents repeating them while improvement work is still draft.

## Alternatives considered

- Treat full-store migration as deferred only under BM25 work — rejected for agent guidance; the directory migrate path already exists and must be documented correctly now.
- Auto-synthesise claims in CLI — rejected for this decision (agent review remains required); may be explored later under the improve work.

## Consequences

- Atlas `remember` path and SKILL.md should cite these lessons when describing migrate/promote.
- Implement of `atlas-migrate-cli-improve-v1` starts only after design plan approval (Autogenesis gate).
