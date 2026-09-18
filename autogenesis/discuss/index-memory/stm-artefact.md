---
type: document
title: "1-by-1 — which artefact is short-term memory"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: settled
kva: alive
reality: current
description: "Live choice: folder indexes, a Fresh section on root index.md, or working-memory.md."
tags: [index-md, stm, decision-pending]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
  - path: autogenesis/discuss/index-memory/requirements.md
    kind: related
---

## Context

First hub batch item, taken 1-by-1. The human asked for the full picture before choosing what the working-memory artefact is.

The locked objective still needs a first focal point for query, and a place to add new memories. This page only decides which file that is.

## What exists today

Atlas already has three different things people call an index.

1. **Folder `index.md`.** Reserved OKF name. Every folder that holds concept pages is expected to have one. Compile check `index_md_present` fails if it is missing. The skill contract also names `index_md_listing`: the file should list the concept pages and child folders. These files are a map of what lives in the folder, not a recency list. Example: discuss `autogenesis/plans/index.md` lists every plan.

2. **Store-root `index.md`.** The same reserved name at the Atlas root. Today it is a short map of top-level folders. Agents can open it first because it is small and already required.

3. **Recall index.** A machine generation under `.atlas-index` for SCHEMA 2.0 ranked search (`atlas recall index build`). It is not markdown. It is not the notebook. Mixing it with STM would hide the working set from a human reader.

A cheap probe: if STM *is* the folder `index.md` files, then removing a line to “forget” makes the inventory incomplete. Completeness and a bounded notebook fight each other in one list.

## Options

### A — Every folder `index.md` is STM

Query would walk those listings as the near memory. New pages already get a folder-index line when remember is tidy.

Cost: forget cannot drop a line without a compile miss. Order cannot mean frequency, because the listing must stay complete. “Scan index first” is ambiguous when there are many folder indexes.

### B — Fresh section on root `index.md` (recommended)

Root `index.md` keeps the folder map, and gains an ordered **Fresh** list of working-set pages. Query reads that section first. Remember appends a new page there after compile green. Folder indexes stay complete inventories.

Cost: one file, two jobs. The skill text must say “read Fresh, do not treat the folder map as STM.” Honours the user’s wording that `index.md` is the near notebook.

### C — Dedicated `working-memory.md`

A new page is the only STM list. Root and folder indexes stay maps. Query is taught a new first file.

Cost: cleaner split, extra artefact, and the name `index.md` is no longer the notebook. Easier forget later, because dropping a line never touches compile inventory.

## Decision

**A.** Every folder `index.md` is short-term memory. That is the purpose of this work. Options B and C are not current reality.

Query must treat those files as the near notebook. New memories are added to the folder index that owns them, not to a side list.

## Consequence now live

If folder indexes stay *complete* inventories, they already name every concept page. Then “search files not in index.md” has nothing to search. Two-layer recall only survives if either the bodies are the deep layer (indexes stay maps), or the indexes become *incomplete* working sets (compile listing rules change).

## Outcome

Pin A is alive. Next 1-by-1 is what layer 2 means under A.
