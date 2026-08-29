---
type: document
title: "Precedent — APM GitHub auth chain"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Grounded in microsoft/apm AuthResolver + GitHubTokenManager and getting-started/authentication.md."
origin: third-party
sensitivity: public
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Checked `microsoft/apm` on GitHub (default branch SHA `6be370d`). The living source of truth is not the marketing page alone.

Code:

- `src/apm_cli/core/auth.py` — `AuthResolver` is the single class every remote operation must use. Resolves per `(host, port, org, optional path)`. Returns frozen-ish `AuthContext`: `token`, `source`, `token_type`, `host_info`, `git_env`, `auth_scheme`.
- `src/apm_cli/core/token_manager.py` — `GitHubTokenManager` does the env walk plus `gh auth token --hostname <host>` and `git credential fill`.
- Docs in-tree: `docs/src/content/docs/getting-started/authentication.md`.
- Agent note: `.apm/skills/auth/SKILL.md` and `.apm/agents/auth-expert.agent.md`.

GitHub-class chain in `_resolve_token` (matches the docs table):

1. `GITHUB_APM_PAT_{ORG}` (org uppercased, hyphens to underscores)
2. `GITHUB_APM_PAT` → `GITHUB_TOKEN` → `GH_TOKEN`
3. `gh auth token --hostname <host>` (skipped if `gh` missing or host not GitHub-class)
4. `git credential fill` with `protocol=https` and `host=` (port embedded as `host:port`)

Other host classes do **not** reuse GitHub env vars: GitLab has its own pair; generic hosts are credential-helper only; ADO is `ADO_APM_PAT` then `az` bearer on cloud only.

Hard constraints in code/docs that matter for Atlas:

- Token-bearing git traffic is HTTPS. SSH is a separate transport decision (`APM_GIT_PROTOCOL`, `--ssh`/`--https`). APM does not pick SSH keys; it uses the machine agent.
- Public `github.com` tries anonymous first (helpers and auth headers fenced). 401/403/404 unlock the chain. DNS/TLS/timeout/throttle do not.
- Child git env is non-interactive: `GIT_TERMINAL_PROMPT=0`, `GIT_ASKPASS=echo`, platform token env vars blanked so they cannot leak into the subprocess, token injected as `GIT_TOKEN` or an Authorization header.
- Docs sentence to keep: authentication and transport are independent decisions.

Atlas implication: the helper the user asked for is an `AuthResolver`-shaped object keyed by host/org from a scheme-free atlas-id, emitting `git_env` — not a full clone URL baked into the id.

## Provenance

- https://github.com/microsoft/apm/blob/main/src/apm_cli/core/auth.py
- https://github.com/microsoft/apm/blob/main/src/apm_cli/core/token_manager.py
- https://github.com/microsoft/apm/blob/main/docs/src/content/docs/getting-started/authentication.md
- https://microsoft.github.io/apm/getting-started/authentication/
