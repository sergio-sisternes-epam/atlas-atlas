---
type: experience
title: "2026-08-30 private HTTPS submodule mount: GitHub rejects extraHeader"
created: 2026-08-30
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: raw
description: "Autogenesis hit invalid credentials on atlas mount --target references/atlas. Cause was git http.extraHeader Authorization. Fix: gh credential helper; token insteadOf only without gh."
origin: internal
sensitivity: internal
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: lessons/2026-08-30-github-rejects-git-extraheader.md
    kind: records
  - path: recipes/git-update-mounted-store.md
    kind: related
  - path: experiences/2026-08-30-first-submodule-store-write.md
    kind: follows
---

## Context

Storage-mesh MVP landed `atlas mount` but live private-remote mount was not exercised. Autogenesis packaging mounted `github.com/sergio-sisternes-epam/autogenesis-atlas --ref main --target references/atlas` inside a git skill worktree. `gh` had a `repo` token. Plain `git submodule add` worked; `atlas mount` did not.

## What happened

Mount ran `git -c http.extraHeader=Authorization: <token> submodule add`. GitHub returned `invalid credentials` for the private HTTPS URL. Default dest under gitignored `.atlas/` had already been switched to clone. Copilot then asked to prefer the resolved PAT; Autogenesis showed extraHeader still fails even when GH_TOKEN looks valid. Auth now prefers `credential.helper=!gh auth git-credential` when `gh` is on PATH (and drops a stale GH_TOKEN so it cannot override gh). Token `url.insteadOf` is only the no-gh fallback. Never extraHeader. Smoke: throwaway git repo, same Autogenesis pointer and `--target references/atlas` → exit 0, gitlink, `.gitmodules`, `atlas-mesh.json`. Atlas skill PR https://github.com/sergio-sisternes-epam/atlas/pull/3.

## Outcome

Private `--target references/atlas` submodule mounts work with gh. Autogenesis kept its hand-rolled gitlink; future mounts use the fixed CLI. Claim: do not send `http.extraHeader=Authorization` on GitHub HTTPS clone or submodule add.
