---
type: document
title: "Current reality — Atlas schema governance pins"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Settled pins from the schema-governance conversation. Not implement authority."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: autogenesis/discuss/schema-governance/pin-frame.md
    kind: records
  - path: autogenesis/discuss/schema-governance/pin-contribute.md
    kind: records
  - path: autogenesis/discuss/schema-governance/pin-extension-home.md
    kind: records
  - path: autogenesis/discuss/schema-governance/pin-root-layout.md
    kind: records
  - path: autogenesis/discuss/schema-governance/pin-path-cli.md
    kind: records
  - path: autogenesis/discuss/schema-governance/pin-project-overlays.md
    kind: records
  - path: autogenesis/discuss/compile-type-contract/init-surface.md
    kind: related
---

## Content

Current reality for this orbit (not product-implemented):

1. One governance surface: SCHEMA keys, templates, root layout, init, and a schema path.
2. Skill-owned stores may extend locally. Host install is an explicit, compile-checked contribution.
3. Core SCHEMA.json stays closed. Extras live in overlay files. Compile merges. Core-key clash fails.
4. Knowledge pages keep free layout. Install may only write claimed prefixes; undeclared root files fail compile.
5. Schema path tells the agent when. CLI (`init`, `schema install`, `schema new`) is the only writer. Pin F stands.
6. Agents may `schema new` a bespoke overlay on a project Atlas before a skill exists. Same gates. Later skill-isation is moving that overlay into the skill package.
7. Overlays add types only; they do not mutate core `templates.by_type`.
8. Compile and uninstall use a CLI write-receipt, not `claimed_folders` alone.
9. Uninstall does not delete pages authored after install.
10. Replacing an overlay that changes its own required keys is compile-critical unless `--force`. No Buf-class checker in this work.

This page is lineage, not implement authority. Atlas product path `schema` and CLI verbs remain unbuilt. Operator confirmed pins 13–16 one-by-one. Design still waits for explicit implement approval.

## Provenance

From-conversation pass 2026-09-03 into atlas-atlas.
