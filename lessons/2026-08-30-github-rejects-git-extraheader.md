---
type: lesson
title: "Do not set git http.extraHeader Authorization for GitHub HTTPS"
created: 2026-08-30
status: settled
work_id: 2026-08-29-atlas-storage-mesh-mvp
description: "GitHub private clone and submodule add reject Authorization extraHeader (invalid credentials). Use gh auth git-credential, or x-access-token insteadOf when gh is absent."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: experiences/2026-08-30-private-https-submodule-mount.md
    kind: derived_from
---

## Content

**Do:** `git -c credential.helper= -c credential.helper=!gh auth git-credential submodule add` (or clone) when `gh` is on PATH. Drop `GH_TOKEN` / `GITHUB_TOKEN` for that process if a stale env token would override gh. Without gh, `url.https://x-access-token:<token>@github.com/.insteadOf=https://github.com/` is the fallback.

**Avoid:** `git -c http.extraHeader=Authorization: Bearer|token <pat> clone|submodule add`. GitHub answers `remote: invalid credentials` on private HTTPS even when `gh auth status` shows a valid `repo` token. ExtraHeader is not a substitute for the gh HTTPS helper.
