---
type: experience
title: "2026-09-03 Autogenesis consult — write-home impact and migrate sequence"
created: "2026-09-03"
work_id: "2026-09-03-skill-mount-home"
status: raw
description: "Autogenesis session Atlas mount impact: own-store still references/atlas; persist to autogenesis-atlas failed; migrate-now vs defer."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: experiences/2026-09-03-implement-skill-mount-home.md
    kind: follows
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
  - path: decisions/consuming-skill-atlas-activation-card.md
    kind: related
---

## Context

Operator asked a fresh Autogenesis session to discuss Atlas 0.8.5 write-home impact. That session did not persist into autogenesis-atlas: worktree gitlink `references/atlas` was empty, `.atlas/` gitignored, discussion/plan must not edit product `.gitmodules`.

## What happened

Autogenesis 0.3.13 still mounts `github.com/sergio-sisternes-epam/autogenesis-atlas` at `references/atlas`. Loaded Atlas skill on that machine was 0.8.1 (no path `mount`); contract was read from this 0.8.5 worktree.

Impact: Discussion fail-closed without subject SCHEMA; Run/G2/Exit use the same resolver so wrong root leaks or G2 is incomplete. APM install still clones the gitlink into `~/.agents/skills/autogenesis`.

**Migrate now** (one Autogenesis Run after Atlas 0.8.5 is loaded): SKILL + workflow-discipline + discuss load Atlas path `mount` with `atlas_id=github.com/sergio-sisternes-epam/autogenesis-atlas`; move gitlink to `.atlas/github.com/sergio-sisternes-epam/autogenesis-atlas`; drop `.gitignore` `.atlas/`; docs; construct smoke; two PRs (store then parent).

**Defer:** other-subject `<subject>/references/atlas/`; learn-skill probe; research; okf-conformance; atlas-migrate auto-initiate (collides with path `init`); think-ramble string; discuss adversarial suites; skill-side `references/atlas.md` pointer.

Recommended answers to their open questions: other-subject G2 later; follow Atlas two-PR gitlink (not zero gitlink); skip `references/atlas.md`; block Autogenesis implement until Atlas 0.8.5 is the loaded skill.

The later pin resolved how consuming skills retain the reference: their main
`SKILL.md` carries the exact Atlas `path: mount` card with `atlas_id` and
`ref`. Atlas `init` and `migrate` stamp it; Autogenesis should consume that
contract during its own-store migration rather than inventing a local pointer.

## Outcome

Picture accepted into this store. Autogenesis own-store hardening is leftover work on the autogenesis skill, not this package.
