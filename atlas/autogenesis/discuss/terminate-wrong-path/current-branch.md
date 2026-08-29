---
type: document
title: "How to formalise terminate-wrong-path"
created: 2026-08-27
work_id: 2026-08-27-terminate-wrong-path-behaviour
status: settled
kva: alive
reality: current
description: "A+B pinned and shipped. Discuss terminate plus Atlas remember recipe."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/terminate-wrong-path/hub.md
    kind: derived_from
  - path: work/2026-08-27-terminate-wrong-path-behaviour.md
    kind: implements
  - path: atlas-project/wrong-path-agent-memory-layer/exit-wrong-comparison.md
    kind: related
---

## Content

Worked example already in the store:

1. Persist the wrong frame as its own folder/branch (`kva: terminated`).
2. Keep useful debris as archive notes (`scan-2026.md`, `kva: alive`, `reality: archive`).
3. Write an exit-reason document (`kva_role: exit-reason`, `kva: alive`).
4. Subject uses `kind: kva_terminate` → exit node.
5. Exit node links **back** to living vision and correct comparison.
6. Do not flip terminated pages to forming; reactivation is a new page.

### Options under discussion (not pinned)

- **A — Discuss path verb** `terminate` (or `exit-ramp`) beside sprout/lint/from-conversation. Natural home: KVA already lives in discuss.
- **B — Atlas remember recipe** that remember/work must run when the user says the path was wrong. Keeps discuss thin.
- **C — Autogenesis path** `correct` that may be entered from discussion or from design review (`stage: design`, same `work_id`). Stronger workflow-discipline fit; risk of a fourth skill owning KVA.
- **D — Document-only convention** (what we just did by hand). Fastest; will drift.

**Pinned and shipped:** A+B. Discuss path `terminate` is the mechanism. Atlas remember loads it on explicit trigger. Query will not treat terminated pages as current guidance.

### Parked

- Compile-enforced `kva_terminate` target (lint L4 is v1).
- agent-spec Gherkin — leaf `p-agent-spec-terminate.md`.

## Related

Settled on A+B. Product files: discuss `terminate` path; Atlas remember step 2 and recipe.
