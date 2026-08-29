---
type: decision
title: "MVP URI split — parse then two-segment host profile"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "atlas:// is RFC URI. Id = host + two path segments for GitHub-shaped hosts. Nested groups later via longest-prefix."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/uri-id-extract.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/atlas-uri-vs-hash.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-uri-nested-groups.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

MVP for `atlas://` pointers:

1. Parse as a URI. Scheme `atlas`. Host is the authority. `#` is a heading fragment only. Path is slash-separated.
2. Peel the atlas-id with the **same rule as `normalise`**: host plus the next **two** path segments (`org`/`repo`). Remainder is the in-store path (relative to mesh `subpath`).
3. Host profile for MVP: `github.com`, `*.ghe.com`, and any other host **default to that two-segment width**. Fewer than two segments → error.
4. No hunting regex. No reserved-word scan of the page path (`tree`, `.git`, …).
5. This is known to be incomplete for nested-group forges (GitLab `group/sub/project`, and similar). Expansion is **longest prefix of `host+path` that matches a known atlas-id**, plus per-host width tables. That work is a forming leaf, not a silent extra in MVP.

Same-store links stay relative Markdown. Cross-store links use this URI.
---
