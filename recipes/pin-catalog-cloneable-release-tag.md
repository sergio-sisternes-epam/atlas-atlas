---
type: recipe
title: "Pin atlas-marketplace packages to cloneable release tags"
created: 2026-09-14
description: "Verify tag^{} matches the intended commit, set apm.yml ref to v{version}, apm pack 0.30.0, commit generated marketplace.json, do not prefer SHA as ref."
origin: derived
sensitivity: public
kva: alive
work_id: 2026-09-14-copilot-sha-ref-install
relates_to:
  - path: work/2026-09-14-copilot-sha-ref-install.md
    kind: implements
  - path: experiences/2026-09-14-copilot-sha-ref-install.md
    kind: derived_from
  - path: lessons/2026-09-14-catalog-ref-must-be-cloneable-tag.md
    kind: related
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
---

## Content

1. Confirm the published GitHub release tag for the package version
   (`v{version}`).
2. Peel it: annotated tags resolve to a tag object first, then `tag^{}` is
   the commit. Lightweight tags already point at the commit.
3. Set only `marketplace.packages[]` in `apm.yml` (`name`, `source`,
   `version`, cloneable `ref`, `description`). Keep `version` aligned with
   the package manifest at the peeled commit.
4. Do not vendor package source. Do not edit
   `.claude-plugin/marketplace.json` by hand.
5. `apm pack` with apm-cli 0.30.0. Commit `apm.yml` with the generated
   catalog.
6. Align `AGENTS.md`, `CHANGELOG.md` (`Unreleased`), `CONTRIBUTING.md`, and
   `README.md`. Document peeled commits for provenance; do not call pack
   `sha` the peeled commit when the tag is annotated.
7. Open a PR against `main`. Wait for `validate-and-pack`. Merge publishes.

Sources: [atlas-marketplace#33](https://github.com/sergio-sisternes-epam/atlas-marketplace/issues/33),
[atlas-marketplace#34](https://github.com/sergio-sisternes-epam/atlas-marketplace/pull/34).
