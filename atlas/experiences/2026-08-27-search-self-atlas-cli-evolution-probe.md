---
type: experience
title: "2026-08-27 search self-Atlas: CLI evolution probe"
created: 2026-08-27
work_id: atlas-bm25-and-live-migration-v1
status: raw
description: "Second query-path probe. Natural-language 'how did the CLI evolve' was still multi-hop. Store phrases cli surface and type:experience listed the phase spine. No single evolution page exists."
origin: internal
sensitivity: internal
tags:
  - atlas
  - search
  - query-path
  - cli
relates_to:
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: implements
  - path: experiences/2026-08-27-search-self-atlas-bm25-hard-query.md
    kind: follows
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: related
  - path: experiences/2026-08-27-implement-atlas-compile-focus-lenses.md
    kind: related
---

## Context

Follow-up to the hard BM25-ideas query. User asked an “easier” question: how the Atlas CLI surface evolved and what drove the change. Goal was to test the harness-before-BM25 hypothesis before Autogenesis design.

## What happened

Natural sentence `how did our cli surface evolve what drove that change` ranked plans that contain the words *how / change / cli* (focus-lenses plan, migrate-CLI plan), not the Phase 1–6 spine.

Phrase `cli surface` and filter `CLI type:experience` listed Phase 2–4 implements, migrate lessons, 0.7.5 type-contract, 0.7.6 focus lenses.

Synthesis still required reading those pages plus `cli-compile-list-review.md`. Cost: 3 searches, ~6 page reads (BM25 hunt: ~6 searches, ~10 reads).

## Outcome

Easier than “all ideas on BM25.” Not one-search-one-page. Titles on the *pieces* are good; the *question class* (evolution / why) has no hub page.

Drivers on those pages: reboot pins → verbs; user grep pilot → search; live migrate pain → lessons; 27-protostar miss → `type:` and `--list-type`; operator review → drop `--list-type`, add compile `--type/--path`.
