---
type: work
title: "Pin atlas-marketplace catalog refs to cloneable release tags"
created: "2026-09-14"
work_id: "2026-09-14-copilot-sha-ref-install"
status: done
description: "Copilot plugin install failed on SHA refs; catalog now pins cloneable v{version} tags. Issue 33, merged PR 34."
origin: derived
sensitivity: public
relates_to:
  - path: experiences/2026-09-14-copilot-sha-ref-install.md
    kind: records
  - path: lessons/2026-09-14-catalog-ref-must-be-cloneable-tag.md
    kind: related
  - path: recipes/pin-catalog-cloneable-release-tag.md
    kind: related
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: follows
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: related
---

## Scope

Fix atlas-marketplace catalog pins so GitHub Copilot plugin install can
`git clone --depth 1 --branch <ref>`. Link the GitHub issue and merged PR.

## Status

Opened and closed 2026-09-14. Marketplace PR 34 merged to `main`.

## Outcomes

- Catalog `marketplace.packages[].ref` is the published release tag matching
  `version` (`v{version}`).
- Generated `.claude-plugin/marketplace.json` has tag `ref` plus pack `sha`.
- CONTRIBUTING no longer prefers raw SHA as `ref`.
- Issue: https://github.com/sergio-sisternes-epam/atlas-marketplace/issues/33
- PR: https://github.com/sergio-sisternes-epam/atlas-marketplace/pull/34

## Related

- experiences/2026-09-14-copilot-sha-ref-install.md
- lessons/2026-09-14-catalog-ref-must-be-cloneable-tag.md
- recipes/pin-catalog-cloneable-release-tag.md
