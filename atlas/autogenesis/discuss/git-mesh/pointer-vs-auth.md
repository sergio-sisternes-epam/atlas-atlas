---
type: document
title: "Lean — MD pointers vs atlas auth alias"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Links in markdown are locators. Git access uses an atlas auth alias plus a translation engine. Resolves contradiction 2."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-protocol-guess.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-helper-surface.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Content

User lean 2026-08-29 on contradiction 2:

- **Do not bake authentication into Markdown links.** A link in an OKF page may be a valid pointer (`https://github.com/org/repo/...`, `atlas://github.com/org/repo/...`, scheme-free host/path). That string locates knowledge. It is not a credential and not “the” clone protocol for this machine.
- **Authentication is an alias** the user registers with something like `atlas auth` against a git remote (host, and maybe org).
- Atlas owns a **translation engine**: pointer in MD / mesh id → resolved auth alias → *this process’s* authenticated git remote (HTTPS+token, SSH, …).

This splits the old fight:

| Layer | Who owns it |
|-------|-------------|
| Pointer | page / mesh / `atlas://` |
| Auth alias | `atlas auth` (user, host-scoped) |
| Transport URL used right now | translation engine, not the MD file |

It counters “Atlas cannot help with checkout because protocol is unknown.” Protocol is unknown *in the page*. It is known *after* auth is configured for that host.

It does not put `https://` back into atlas-id. Id can stay scheme-free; MD may still *display* a full URL as a pointer.
