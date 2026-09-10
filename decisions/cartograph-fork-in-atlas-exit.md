---
type: document
title: "Retire the historical in-Atlas Cartograph location"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: settled
kva_role: exit-reason
kva: alive
origin: derived
sensitivity: internal
description: "Formal exit reason for the old Build-fork location; current help uses the standalone Copilot Cartograph package."
relates_to:
  - path: decisions/cartograph-fork-in-atlas.md
    kind: records
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: help/cartograph.md
    kind: related
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/apm.yml
---

# Retired location guidance

The user explicitly requested retiring the old location memory on 2026-09-10.
The objective is accurate present-day Atlas help, particularly installation
and opening of Cartograph in GitHub Copilot.

The claim that Cartograph lives only under `atlas/addons/cartograph/` belongs
to the 2026-08-23 Build-fork decision. It must not direct current Copilot
installation or imply that users need a copy of the Atlas skill's source.
Current source identifies the separate
`sergio-sisternes-epam/atlas-cartograph` APM package and its self-contained
canvas runtime.

This is a **supersession**, not a claim that the historical decision was
never valid: it had an earlier Build context and now has a documented
successor. The old page retains `kva: superseded` and exactly one
`kva_supersede` edge to this living exit-reason page. Its body is preserved
for historical explanation and is excluded from ordinary Atlas search.

Use the [current package memory](../autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md)
and [Cartograph help](../help/cartograph.md) instead. The earlier status-only
retirement is now completed with the formal reason node; the inline
`exit_reason` string has been removed from the old page.

The forming Graphify inspiration page's Cartograph navigation edge was
redirected to the living successor so the exit stub does not retain an
active protostar shortcut. Its proposed ideas remain forming and unchanged.

This exit concerns Cartograph's former location inside Atlas. It does not
change Atlas store-mount locations, erase historical experiences, install
packages, or approve the pending help/visualise runtime design.
