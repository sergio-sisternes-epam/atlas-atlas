---
type: document
title: "Design thinking — atlas resolve and atlas checkout"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: current
description: "User design: resolve maps remote to local; checkout is explicit; submodule under .atlas/<kebab>; branch in mesh; contribute via PR."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/id-to-checkout-join.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-agents-location.md
    kind: related
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

User design (forming, not implemented):

1. `atlas resolve` translates a remote locator to a local file path when that Atlas is already checked out.
2. If it is not checked out, the user runs `atlas checkout` and **passes the remote URL**. Atlas does not invent the protocol. The protocol is whatever is in that URL.
3. Checkout materialises a **git submodule** at `.atlas/<atlas-repo-url-kebab-case>/`.
4. Checkout also pins a **branch**. Branch and the checkout URL live in the mesh configuration.
5. Contribution is the submodule itself: edit, commit, open a pull request on the Atlas repo. No separate worktree story required for MVP.

Split that this implies:

- atlas-id stays scheme-free host/path (where knowledge lives).
- checkout URL is a mesh field (how this machine fetched it).
- local root is derived from a kebab encoding of the repo locator.
- resolve never clones; checkout never guesses ssh vs https.
