---
type: document
title: "Design thinking — Atlas as its own repo, atlas install, git is the overlay"
created: 2026-08-28
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Move Atlas stores into first-class repos like APM. atlas install materialises them. Skills stay lean. Mesh composes via APM deps."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/tension-checkout-lifecycle.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-package-shape.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

User design 2026-08-28 (forming):

- Every Atlas lives in its **own git repository**, same grain as an APM package — not only `references/atlas/` buried inside a skill tree.
- Layout may be **monorepo** (several Atlas roots in one repo) or **multirepo** (one Atlas per repo). Both stay on the table.
- The materialise verb is **`atlas install`**: check a git repo out to a specific folder. If the working tree is already a git repo, the checkout is a **submodule**. If not, a plain clone is enough.
- Agents write **directly in that folder**. There is no second overlay tree. **Git is the overlay.** Changes leave through PR / merge.
- A skill stays lean: skill text says *what* the knowledge is and *how* to use it; the Atlas trees are declared checkout/install config and materialised only for identities the user can authenticate.
- No permission on the remote → no local tree → no access. Auth remains the gate, not an extra ACL inside Atlas.
- Every successful install is registered on the **mesh**.
- A skill may also ship a mesh by depending on other **APM packages** that themselves contain Atlas definitions.

This tightens the original three-layer stack: APM distributes packages; `atlas install` materialises OKF trees; mesh + `atlas://` connect them; git records writes.
