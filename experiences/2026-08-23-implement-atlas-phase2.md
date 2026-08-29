---
type: experience
title: "2026-08-23 implement Phase 2: atlas validate/compile Python CLI"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Phase 2 — agent-cli layout prototype: SCHEMA gate, staging-empty hard fail, not-just-links, default templates, mini-atlas fixture smokes green."
tags: "[memory, implement, atlas, cli, work_id]"
origin: internal
sensitivity: internal
implements: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
plan_path: /home/workdir/artifacts/autogenesis-plans/2026-08-23-atlas-reboot-okf-wiki-v1.md
construct_eval: deferred
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: experiences/2026-08-23-atlas-design-plan.md
    kind: implements
  - path: experiences/2026-08-23-implement-atlas-phase1.md
    kind: follows
---
# 2026-08-23 implement Phase 2: atlas validate/compile CLI

## Context

Phase 1 delivered skill skeleton, adversarial scenario, SCHEMA contract. Phase 2 builds the first deterministic gate agents can call.

## What was implemented

### Changed files

- `atlas/scripts/atlas.py` — shim entrypoint
- `atlas/scripts/atlas_cli/` — agent-cli layout (`cli.py`, `commands/validate.py`, `core/{paths,frontmatter,schema}.py`)
- `atlas/references/templates/experience.md` — default template with frontmatter rules copy
- `atlas/references/templates/decision.md` — default template
- `atlas/fixtures/mini-atlas/` — SCHEMA.json, indexes, sample decision + experience
- `atlas/SKILL.md` — version 0.2.0-phase2, CLI usage note

### Smokes exercised

| Smoke | Result |
|-------|--------|
| Clean mini-atlas validate | exit 0 |
| Non-empty staging | exit 2, `no_answerable_in_staging` |
| Thin link-list page | exit 2, `not_just_links` |
| Missing SCHEMA.json | exit 2, `schema_present` |

### Deferred

- BM25 search / Rust binary
- mesh consolidation in compile
- atlas migrate / promote commands
- construct adversarial run (still deferred until more of CLI surface exists)
- section-level template enforcement (frontmatter simplicity budget is read; section body checks not yet)

## Outcome

Agents can run:

```bash
python3 /home/workdir/.grok/skills/atlas/scripts/atlas.py validate --root <atlas>
python3 /home/workdir/.grok/skills/atlas/scripts/atlas.py compile --root <atlas>
```

Compile stays red while staging has files — matching the approved Structure + Compile pins.

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **implements:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **follows:** [2026-08-23-implement-atlas-phase1](2026-08-23-implement-atlas-phase1.md)
