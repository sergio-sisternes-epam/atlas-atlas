---
type: experience
title: "Cartograph ported into Atlas as Build viewer"
created: 2026-08-23
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
status: done
description: "Forked okf-wiki graph-viewer into atlas/addons/cartograph; Atlas-native scan, skill-only source, crawl, welcome gate, hyperspace arrival."
tags:
  - cartograph
  - viewer
  - port
  - build
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: decisions/cartograph-fork-in-atlas.md
    kind: records
  - path: decisions/atlas-name.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase6.md
    kind: follows
---

## Context

okf-wiki shipped an optional Grok Build star-map (`addons/graph-viewer`). Atlas needed the same sky without remaining bound to `knowledge/` · `SCHEMA.md` folders, and without a second copy of Atlas code in the host app.

## What happened

The viewer was forked into `addons/cartograph/` (not a shared module). Scan now detects `SCHEMA.json`, walks free layout (skipping `staging/` · `templates/` · `mesh/`), treats `relates_to` as authoritative edges, and resolves `atlas://` mesh links. Legacy okf-wiki stores still open.

The Build host imports `@atlas/cartograph` from the skill (symlink, not a copy). Opening sequence is crawl → welcome list of Atlas-compatible skills → hyperspace drop into the chosen galaxy. `atlas view --root` points the preview at a store.

## Outcome

Cartograph is Atlas-owned. Skill process memory and fixtures render as the live sky. Wiki-compatible skills remain selectable. Compile/search/migrate are unchanged; the add-on stays optional (`STRIP.md`).

## Related

- **implements:** [Atlas reboot of okf-wiki](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **records:** [Cartograph lives only in the Atlas skill](../decisions/cartograph-fork-in-atlas.md)
- **related:** [Successor name is Atlas](../decisions/atlas-name.md)
- **follows:** [Implement phase 6](2026-08-23-implement-atlas-phase6.md)

## Follow-ups

Keep bundled snapshots of this Atlas in sync when process memory changes. Do not re-copy viewer source into host apps.
