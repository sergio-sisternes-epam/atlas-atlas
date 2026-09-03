---
type: document
title: "Pin — no git repository means refuse to persist"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "Fail-fast for the locked objective. Headless or chat-only sessions do not fall back to skill-internal memory or a user-global cache."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-not-store.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-objective.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
---

## Content

Operator pinned: if there is no active git repository, **refuse to persist**. Do not write. Do not mount.

Rejected here:

- User-global cache as a quiet overflow.
- Skill-internal `references/atlas` as a fallback (that is the leak this orbit exists to close).

This matches git-mesh “git is the overlay; headless degrades” and makes the degradation loud: no repo, no Atlas write. Query of an already-mounted store is a separate question, not pinned here.

### Outcome

KVA alive. Remaining batch item is the `.atlas` shape: a pointer file as stated, or the living `.atlas/<encoded-id>/` directory.
