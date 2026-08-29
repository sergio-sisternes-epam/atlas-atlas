---
type: work
title: "Formalise terminate-wrong-path after discussion"
created: 2026-08-27
work_id: 2026-08-27-terminate-wrong-path-behaviour
status: done
description: "Discuss path terminate plus Atlas remember recipe shipped (A+B). User approved 2026-08-27."
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: follows
  - path: atlas-project/wrong-path-agent-memory-layer/exit-wrong-comparison.md
    kind: related
---

## Scope

Design (not implement) a reusable activation path for: discussion produced a useful-but-wrong frame → persist the frame as terminated knowledge → write an exit-reason node → point back at the living vision / correct comparison → do not delete the wrong branch.

## Status

**done** — A+B implemented: `discuss/references/paths/terminate.md`; Atlas `remember` step 2 + `references/recipes/terminate-wrong-path.md`; query skips terminated frames as current guidance.

## Outcomes

- Discuss 0.3.2 path registry includes `terminate`.
- Atlas 0.7.3 hard rule 9 + remember trigger + query selection rule.
- Worked example in `atlas-project/wrong-path-agent-memory-layer/` unchanged and still the reference persist.

## Related

Depends on the vision cluster as the first worked example of the behaviour.
