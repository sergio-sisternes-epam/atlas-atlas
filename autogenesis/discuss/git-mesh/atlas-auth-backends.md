---
type: document
title: "How atlas auth talks to gh and to other git hosts"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "gh is a backend for GitHub-family hosts. Other/self-hosted use host + token|ssh|git-credential. Forming."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-auth-grain.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: backed_by
  - path: autogenesis/discuss/git-mesh/apm-env-outranks-gh.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-protocol-choice.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Content

`atlas auth` does not wrap every forge’s CLI. It stores an alias `{host, org?, backend, transport}` and, at mount time, asks that backend for a usable git remote + env.

### GitHub family (`gh`)

Hosts: `github.com`, GitHub Enterprise Cloud (`*.ghe.com`), GHES when `gh` has `--hostname` for that server.

Integration (no product coupling to APM):

1. `atlas auth login --host github.com` detects `gh` on PATH.
2. If `gh auth status --hostname <host>` is logged in, Atlas records backend=`gh` and does **not** copy the token into Atlas config. At mount, it runs `gh auth token --hostname <host>` (or sets `GH_HOST`) and builds an HTTPS remote. Same pattern APM’s `AuthResolver` uses.
3. **`gh` is preferred, not mandatory**, even on GitHub-family hosts. PAT fallback is first-class (APM-like): `backend=token` via `--token` or env. Needed when `gh` cannot hold a second account (other enterprise/org), when `gh` is missing, or in CI.
4. Do not force `gh auth login` as the only GitHub path.
5. `--ssh` records transport=ssh, backend=`ssh`. `gh` is unused for the clone; ssh-agent is.

Atlas does not vendor `gh`. It shells out when backend=`gh`. Tokens never go in Markdown.

### Other services and self-hosted

Anything that is a git remote: GitLab, Gitea, Forgejo, Bitbucket, GHES without `gh`, bare `git.company.com`.

Alias key is still **host** (+ optional org). Backend is one of:

| Backend | When | How mount talks to git |
|---------|------|-------------------------|
| `gh` | GitHub-family + `gh` logged in | `gh auth token --hostname` + HTTPS |
| `token` | PAT / deploy token | env or stored secret → HTTPS extraheader / url with userinfo avoided in pages |
| `ssh` | keys in ssh-agent | `git@host:path.git` |
| `git-credential` | host already in git credential helper | `git credential fill` then HTTPS |

`atlas auth login --host git.company.com --ssh`  
`atlas auth login --host gitlab.example --token`

No GitLab CLI required for MVP. A later `glab` backend can appear as another backend name without changing the alias table.

### Classification

Parse the pointer’s host:

- `github.com` / `*.ghe.com` → prefer `gh` if present **and** it is the right account; else `token` or `ssh`
- anything else → `token` or `ssh`; never assume `gh`

Self-hosted GitHub Enterprise: `--host ghe.company.com` and `gh` if the user has `gh auth login --hostname ghe.company.com`. Otherwise `token`/`ssh`.

### What is not stored in Markdown

Tokens, `https://user:pat@host/...` clone URLs, ssh private keys. Pages keep public pointers only.
