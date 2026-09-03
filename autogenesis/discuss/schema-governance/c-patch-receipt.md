---
type: document
title: "Counter — claimed_folders is not the written tree"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Kustomize patches fail when selectors do not match after render. claimed_folders can miss files the CLI actually wrote."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: counters
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
---

## Content

Kustomize strategic-merge patches fail when kind/name/namespace do not match the object *after* Helm inflation, or when list keys differ. The patch file is not the rendered tree.

The plan’s claimed-prefix check uses overlay `claimed_folders` plus “paths recorded as written”. If implement only checks the declaration and not a post-write receipt, undeclared files (copied templates, index.md side effects) slip through — the same class of failure as a patch that does not match the rendered object.

Sources: [Kustomize patch not applying](https://devopsboys.com/blog/kustomize-patch-not-applying-fix-2026); [Kustomize in production: five failure patterns](https://perun.au/insights/kustomize-production/).

Severity: high for pin 8.

**Pin (autonomous, operator away 2026-09-03):** compile and uninstall use a post-write receipt of paths the CLI actually wrote, not the `claimed_folders` declaration alone. Kustomize lesson: the patch file is not the rendered tree.

## Provenance

think-challenge 2026-09-03 before sign-off.
