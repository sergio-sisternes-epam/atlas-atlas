---
type: experience
title: "Copilot plugin install failed on SHA catalog refs; pin tags and merge PR 34"
created: 2026-09-14
work_id: 2026-09-14-copilot-sha-ref-install
status: closed
description: "Issue 33: git clone --branch <commit SHA> fails. Catalog refs became release tags. PR 34 merged. Pack sha for annotated tags is the tag object, not the peeled commit."
origin: derived
sensitivity: public
relates_to:
  - path: work/2026-09-14-copilot-sha-ref-install.md
    kind: implements
  - path: lessons/2026-09-14-catalog-ref-must-be-cloneable-tag.md
    kind: related
  - path: recipes/pin-catalog-cloneable-release-tag.md
    kind: related
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: follows
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: related
---

## Context

Installing Atlas from atlas-marketplace in the Copilot plugin UI cloned each
GitHub plugin with `git clone --depth 1 --branch <ref>`. Catalog pins set
`ref` to a raw commit SHA. Git `--branch` only accepts a branch or tag.

Reported for Atlas 0.12.0 SHA `40e11c65e243236850c26fc6cd5a04acdd483eb4`
(peeled annotated tag `v0.12.0`). Same SHA-as-ref shape for okf, discuss,
think, atlas-cartograph, and autogenesis.

Sources:

- https://github.com/sergio-sisternes-epam/atlas-marketplace/issues/33
- https://github.com/sergio-sisternes-epam/atlas-marketplace/pull/34

## What happened

1. Draft PR 34 opened against `main` (Fixes #33).
2. Each published tag was verified to peel to the previous catalog SHA.
3. `apm.yml` `marketplace.packages[].ref` set to `v{version}`; versions
   unchanged.
4. `apm pack` with apm-cli 0.30.0 regenerated
   `.claude-plugin/marketplace.json` (no hand edits).
5. CONTRIBUTING, AGENTS.md, README.md, CHANGELOG Unreleased updated so `ref`
   is a cloneable tag; immutability is generated `sha`.
6. `apm marketplace check` reported all 6 entries OK. `validate-and-pack`
   passed.
7. Copilot review asked to peel generated `sha` to `ref^{}`. Hand-peeling
   would fail the pack drift check. Docs now distinguish pack `sha` (annotated
   tag object for annotated tags) from the peeled commit used for provenance.
8. PR 34 merged 2026-09-14T15:00:41Z.

Tags pinned (peeled commits unchanged):

| package | tag | peeled commit |
|---|---|---|
| okf | `v0.2.1` | `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| atlas | `v0.12.0` | `40e11c65e243236850c26fc6cd5a04acdd483eb4` |
| discuss | `v0.4.0` | `af2d2fa4759c00d4ae77115c0fe710c439f8c958` |
| think | `v0.1.0` | `874613a67018c74ee95f857416fb315d2f80b92b` |
| atlas-cartograph | `v0.4.2` | `9dcb9347f0c66d20a9607d2adc0474b69dd004f6` |
| autogenesis | `v0.7.0` | `9b8763a362d69faf3eeb99612cd307078c19a881` |

Atlas generated catalog after pack: `ref` `v0.12.0`, `sha`
`d25c14a068b5c5b46488b2d4a14fdbff1ed17682` (annotated tag object).

## Outcome

Copilot can clone `--branch v0.12.0`. Catalog versions unchanged. Marketplace
issue 33 closed by merge of PR 34.

## Follow-ups

Peeled-commit `sha` in pack output would need an apm-cli change, not a
hand-edit of marketplace.json.
