---
type: experience
title: "2026-08-23 implement Phase 1: Atlas foundation (skill skeleton, scenario, SCHEMA contract)"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Phase 1 implement of approved Atlas design plan — adversarial scenario materialised, atlas skill skeleton, SCHEMA contract shape."
tags: "[memory, implement, atlas, work_id]"
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
  - path: experiences/2026-08-23-okf-wiki-design-challenge-karpathy-realign.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: related
---
# 2026-08-23 implement Phase 1: Atlas foundation

## Context

Design plan approved after think-challenge. User directed proceed with implementation. Change-class new-surface; full Rust CLI out of single-slice scope.

## What was implemented (Phase 1)

### Changed files

- `artifacts/autogenesis-plans/2026-08-23-atlas-reboot-okf-wiki-v1.md` — status approved + accepted challenge deltas
- `okf-wiki/references/scenarios/atlas-reboot-adversarial-v1.yaml` — materialised adversarial draft including challenge smokes
- `atlas/SKILL.md` — successor skill skeleton (contract, CLI target surface, routing to okf, activation cards)
- `atlas/references/SCHEMA.contract.json` — machine contract shape for per-Atlas SCHEMA.json including simplicity budget

### Explicitly deferred (not in this slice)

- Rust `atlas` binary / BM25 implementation
- Live migration of production okf-wiki store content
- Mesh runtime fan-out
- Construct evaluation run (deferred until CLI exists to exercise smokes)

## Outcome

Phase 1 foundation in place. Skill name **Atlas** is now a real skill entry with pinned contracts. Further implement slices must stay within approved plan scope and re-enter implement path as needed.

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **implements:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **related:** [2026-08-23-okf-wiki-design-challenge-karpathy-realign](2026-08-23-okf-wiki-design-challenge-karpathy-realign.md)
- **related:** [2026-08-23-implement-atlas-phase2](2026-08-23-implement-atlas-phase2.md)
