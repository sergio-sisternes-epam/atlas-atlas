---
type: decision
title: "Rename Atlas path query and the search step to recall"
created: 2026-10-04
status: accepted
work_id: 2026-10-03-atlas-memory-layers
origin: user
sensitivity: internal
description: "Sergio, 2026-10-04: path query and the search step become recall. Decision only; the rename is not implemented."
relates_to:
  - path: work/2026-10-03-atlas-memory-layers.md
    kind: implements
  - path: experiences/2026-10-03-implement-atlas-memory-layers.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Decision

Rename the Atlas path `query` and the search step to `recall`, as part of the memory-layers work (skill 0.13.0-beta, product pull request https://github.com/sergio-sisternes-epam/atlas/pull/42).

They are not the same thing today. `query` is the walk: frame, then gist, then page. Search is the step the query receipt still requires (`search_cmd`). Recall is already the name of that walk and of the recall index.

After the rename, the path and the receipt field are both recall, and search is no longer a separate command.

This page records the decision only. The rename is not implemented.

## Rationale

The walk and the receipt step should share one name. Recall already names the walk and the recall index, so keeping a separate path called `query` and a receipt field that still requires `search_cmd` splits one act across two words. Folding both into recall removes the extra command.

## Alternatives considered

- Keep path `query` and rename only the receipt field. Rejected: the path and the step would still disagree.
- Keep search as a separate command beside recall. Rejected: search would remain a second name for the same step.

## Consequences

Skill and product code still say `query` and `search` until a later change. Do not treat this page as the rename. Work hub `work/2026-10-03-atlas-memory-layers.md` stays the cluster for the memory-layers effort; product pull request 42 is not updated by this record.
