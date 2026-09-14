---
type: lesson
title: "Catalog ref must be a cloneable release tag, not a commit SHA"
created: 2026-09-14
status: alive
kva: alive
work_id: 2026-09-14-copilot-sha-ref-install
description: "Copilot and git clone --branch cannot fetch a SHA. Pin marketplace.packages[].ref to v{version}. apm pack 0.30.0 sha may be an annotated tag object."
origin: derived
sensitivity: public
relates_to:
  - path: work/2026-09-14-copilot-sha-ref-install.md
    kind: implements
  - path: experiences/2026-09-14-copilot-sha-ref-install.md
    kind: derived_from
  - path: recipes/pin-catalog-cloneable-release-tag.md
    kind: related
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: related
---

## Content

**Do**

1. Set `marketplace.packages[].ref` to the published release tag that matches
   `version` (Atlas pattern `v{version}`).
2. Verify the tag exists and peels to the intended commit (`tag^{}`) before
   changing the catalog.
3. Run `apm pack` with apm-cli 0.30.0. Commit generated
   `.claude-plugin/marketplace.json` with `apm.yml`. Do not hand-edit it.
4. Treat generated `sha` as the GitHub object pack writes for `ref`
   (annotated tag object ID when the tag is annotated; commit when
   lightweight). Record the peeled commit in the PR for provenance.
5. Keep Copilot clone working: `git clone --depth 1 --branch <tag>`.

**Avoid**

- Raw commit SHA as `ref` (fatal: Remote branch \<sha\> not found).
- Hand-replacing pack `sha` with `ref^{}` (pack drift CI fails).
- Equating pack `sha` with the peeled release commit for annotated tags.

Sources: [atlas-marketplace#33](https://github.com/sergio-sisternes-epam/atlas-marketplace/issues/33),
[atlas-marketplace#34](https://github.com/sergio-sisternes-epam/atlas-marketplace/pull/34).
