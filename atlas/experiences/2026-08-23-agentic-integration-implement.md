---
type: experience
title: "2026-08-23 implement agentic integration (paths + SKILL router)"
created: 2026-08-23
status: done
work_id: atlas-agentic-integration-v1
description: "Shipped query/remember/work path modules, thin SKILL v0.7.0, adversarial scenario; agents must load paths before acting."
relates_to:
  - path: work/atlas-agentic-integration-v1.md
    kind: implements
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: follows
  - path: experiences/2026-08-23-construct-adversarial-green.md
    kind: related
---

## Context

Design plan `atlas-agentic-integration-v1` was approved. Goal: agentic integration so agents follow Atlas CLI and store discipline instead of ad-hoc grep or legacy okf-wiki process alone.

## What happened

Implemented:

- `references/paths/query.md` — search → read → relates_to
- `references/paths/remember.md` — write + compile green + work edges + structural log
- `references/paths/work.md` — work hub lifecycle
- `SKILL.md` v0.7.0 thin router, path registry, hard rules, `activation_card: on`
- Adversarial scenario YAML under `references/scenarios/`

## Outcome

Agents activating Atlas must emit Enter card and load a path module before query or mutation. Format questions still go to skill `okf`.

## Temporary process note

Until live okf-wiki → Atlas migration completes, **prefer Atlas paths** for process memory and knowledge ops on this effort. Do not route new session memory through okf-wiki discipline when Atlas is the intended store.
