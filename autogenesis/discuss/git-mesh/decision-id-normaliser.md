---
type: decision
title: "Deterministic atlas-id normaliser"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Total function pointer → host/org/repo. Ordered steps. Fail closed if the pointer cannot be parsed."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/id-normaliser.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-url-normalisation.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-mount-nested-path.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

Atlas-id is the output of **one deterministic function** `normalise(pointer) → id | error`. Same pointer bytes → same id. Pointers that differ only by the rewrite rules below → same id. No locale-dependent case folding beyond ASCII host letters. Unparseable input → **error**, never a guessed id.

### Algorithm (run in this order)

Input: Unicode string `s`, trimmed of leading/trailing ASCII whitespace. Empty after trim → error.

1. If `s` starts with `atlas://` (ASCII, case-sensitive), drop that prefix. Remainder is still `s`.
2. If `s` matches `git@<host>:<path>` (no `://`), set host=`<host>`, path=`<path>`, go to step 6.
3. If `s` contains `://`, parse as a URI:
   - scheme is discarded (`http`, `https`, `ssh`, `git`, others allowed and discarded)
   - drop userinfo
   - host = URI host; missing host → error
   - drop port if it is `80`, `443`, or `22`; any other port is kept as `host:port` (rare self-hosted)
   - path = URI path
   - query and fragment are **not** part of the id
   - go to step 6
4. If `s` looks like `host/org/repo` or `host/org/repo/...` (no scheme), split on `/`. First segment is host, rest is path. Go to step 6.
5. Else → error.
6. Host: strip a single leading `www.` (ASCII, case-insensitive match); then map ASCII `A-Z` → `a-z` only. Do not fold non-ASCII.
7. Path: strip one trailing `/`. If the last segment equals `.git` (ASCII, case-insensitive) or a segment ends with `.git`, remove only a **trailing** `.git` suffix on the last segment (`Wiki.git` → `Wiki`).
8. Split path on `/` and drop empty segments. Need **at least two** segments (`org`, `repo`). Fewer → error.
9. Id = `host + "/" + org + "/" + repo` using path segments[0] and segments[1] **as-is** (case preserved). Further segments are not in the id (monorepo `subpath`, next gap).
10. In-store path, if the pointer had more (URI path after repo, or `atlas://` remainder after id), is **not** returned by this function. Callers that need a page path parse that separately.

### Invariants

- `https://github.com/sergio-sisternes-epam/atlas-atlas.git` = `git@github.com:sergio-sisternes-epam/atlas-atlas.git` = `atlas://github.com/sergio-sisternes-epam/atlas-atlas` = `github.com/sergio-sisternes-epam/atlas-atlas` → `github.com/sergio-sisternes-epam/atlas-atlas`
- `https://user:x@github.com/Acme/Wiki` → same id
- Mount dir = `.atlas/` + id (nested)
- Function is pure: no git, no network, no auth

## Alternatives considered

- Lowercase org/repo — rejected for MVP; forges differ. Revisit if GitHub-only folding is needed.
- Keep scheme in id — already refuted.
- Best-effort guess on junk input — rejected; fail closed.
---
