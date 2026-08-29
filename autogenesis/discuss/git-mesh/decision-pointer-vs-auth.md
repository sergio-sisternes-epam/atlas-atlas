---
type: decision
title: "Pointers are not credentials — atlas auth translates"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Contradiction 2 pinned. MD/atlas links locate. atlas auth aliases a git remote. Translation engine produces the authenticated remote."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-protocol-guess.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/pointer-vs-auth.md
    kind: records
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-helper-surface.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

Separate **pointers** from **authentication**.

1. Links in Markdown, `atlas://`, and scheme-free atlas-ids are **locators**. They may include `https://` as a human pointer. They are not credentials and not “this machine’s clone protocol.”
2. Users register access with **`atlas auth`** (name may refine later). That stores an **alias** for a git remote (host, possibly org).
3. Atlas has a **translation engine**: pointer → auth alias → authenticated git remote for this process (HTTPS+token, SSH, etc.).
4. Atlas-id stays scheme-free. Protocol never becomes part of identity.

Contradiction 2 is closed as current reality. Pages that argued “paste the clone URL every time because Atlas cannot know protocol” remain in the graph but are not the install path.

## Rationale

Authentication in the link couples a public knowledge pointer to one user’s transport preference. Auth as an alias keeps pages portable and still lets Atlas help with checkout after login.

## Alternatives considered

- Embed scheme in atlas-id — rejected (identity ≠ protocol).
- Require the user to pass a full clone URL on every install and never store auth — rejected as the primary path.
- Auth helper invents https vs ssh from id alone with no prior `atlas auth` — rejected.

## Consequences

- `atlas auth` is now in the agent-verb set (grain host vs org still forming).
- Auth cluster is no longer “should we have a helper?” It is “what does the alias key on, and how does translation parse pointers.”
- Next contradiction in the queue: **#3 `install` vs `checkout`**.
