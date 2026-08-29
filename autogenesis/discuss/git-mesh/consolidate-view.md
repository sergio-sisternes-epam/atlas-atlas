---
type: document
title: "Consolidate view — pieces, gaps, contradictions"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
consolidation: true
description: "Walk-back of the git-mesh discussion. Architecture picture, locked vs lean, protostar gaps, living contradictions."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/scope-storage-not-query.md
    kind: records
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: records
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: records
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: records
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: records
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: records
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: records
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: records
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: records
  - path: autogenesis/discuss/git-mesh/current-reality.md
    kind: records
  - path: autogenesis/discuss/git-mesh/current-mesh-reality.md
    kind: records
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: records
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: records
  - path: autogenesis/discuss/git-mesh/option-c-derived-short.md
    kind: records
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: records
  - path: autogenesis/discuss/git-mesh/option-b-short-primary.md
    kind: records
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: records
  - path: autogenesis/discuss/git-mesh/id-to-checkout-join.md
    kind: records
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: records
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: records
  - path: autogenesis/discuss/git-mesh/apm-env-outranks-gh.md
    kind: records
  - path: autogenesis/discuss/git-mesh/read-microsoft-apm-auth.md
    kind: records
  - path: autogenesis/discuss/git-mesh/retrofit-from-conversation.md
    kind: records
  - path: autogenesis/discuss/git-mesh/exit-aliases-dropped.md
    kind: records
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: related
  - path: autogenesis/discuss/git-mesh/tension-checkout-lifecycle.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-storage-mesh.md
    kind: feeds
---

## Objective (unchanged)

Shape Atlas **storage-mesh composition over git**. Query implementation is out of scope for this discussion, except as an agent-facing verb name.

## Picture

```text
                    ┌─────────────────────────────────────┐
                    │  atlas-id  host/org/repo             │
                    │  (scheme-free; no aliases in MVP)    │
                    └──────────────┬──────────────────────┘
                                   │
          ┌────────────────────────┼────────────────────────┐
          ▼                        ▼                        ▼
   skill process memory      installed corpora         published package
   <skill>/references/atlas  .atlas/<kebab>/           own git repo
   "internal memory"         default --target          APM may ship files
          │                        │                        │
          └──────────── mesh + atlas:// ────────────────────┘
                                   │
                    writes travel by git (commit / PR)
                    agents run Atlas CLI (init, install, query…)
                    APM is a separate product — no hooks
```

Three layers still describe the world, not a combined product:

| Layer | Role now |
|-------|----------|
| Git | Overlay and publish path. There is no second overlay tree. |
| APM | May distribute packages that contain Atlas files. No Atlas API inside APM. |
| Atlas | Identity, mesh, install/init/query, `atlas://`. |

## Locked (alive decisions)

- Scope is storage mesh, not query implementation (`scope-storage-not-query`).
- No cute aliases in MVP. Id must name the server (`drop-aliases-mvp`).
- Atlas and APM stay uncoupled products (`atlas-apm-uncoupled`).

## Current leans (alive documents, not product pins)

- Protocol is not identity. Everyday id is scheme-free `host/org/repo`.
- Skill `references/atlas` = that skill’s internal memory. Other skills may write it. Autogenesis memory = the mesh of those stores.
- `.atlas/` = default install target when the Atlas is *not* skill-internal memory.
- `atlas install` materialises a git tree (submodule if already inside a git repo). Agents write in that folder. Contribute via PR.
- User supplies the real clone URL at install/checkout time. Atlas does not guess https vs ssh.
- Worktree-as-write-mount is not the MVP story.

## Gaps (protostars — discuss later)

Identity / T1

- `p-url-normalisation` — exact string function (host case, `.git`, ssh/https collapse).
- `p-monorepo-id` — `subpath` field vs `#` in the id.
- `p-repo-org-migration` — rename/transfer; deferred on purpose.
- `p-uri-fragment` — `atlas://` vs Markdown `#`.
- `p-unresolved-id-policy` — missing mesh member.

Install / location / T2

- `p-install-vs-checkout` — one verb or two (`install` batch vs `checkout` one-shot).
- `p-atlas-agent-verbs` — required in-session set (init, install, query, git submit; resolve? compile?).
- `p-target-skill` — may install write into a skill package at all?
- `p-skill-knowledge-mesh` — extra corpora via mesh vs extra folders under the skill.
- `p-kebab-encoding` / `p-id-fs-encoding` — directory name for `.atlas/<…>`.
- `p-checkout-parent-git` / `p-submodule-lifecycle` — who owns `.gitmodules`; missing/dirty tree.
- `p-agents-location` — stale name (`.agents/atlas`); still the scope question: project vs user cache.
- `p-apm-git-trace` — after APM copies a skill, which **Atlas** verbs restore a git remote (not an APM hook).
- `p-mono-vs-multi` — one Atlas per repo vs several roots in one repo.
- `p-atlas-package-shape` — knowledge-only package vs skill+atlas.
- `p-mesh-pull` — update already-installed trees.
- `p-optional-git-cut` — what works with no git.

Auth (parked branch)

- `p-auth-precedence` — copy APM env-then-gh, or gh-first.
- `p-auth-protocol-choice` — https vs ssh as transport pref.
- `p-auth-helper-surface` — helper class vs “user always passes URL”.

Terminated (not a gap)

- `p-alias-collision` → `exit-aliases-dropped`.

## Contradictions (design tensions to discuss)

These still fight if taken as simultaneous current reality:

1. **Full-URL identity vs scheme-free identity**  
   `identity-id-is-repo-url` vs `protocol-is-not-identity` / option C. Lean is scheme-free; the original “id becomes the git URL” sentence is not withdrawn in that page.

2. **Guess protocol vs never guess protocol**  
   Auth-helper branch reconstructs clone URLs. Checkout/install design says Atlas cannot help because protocol is unknown. Both cannot be the install path.

3. **`atlas checkout` vs `atlas install`**  
   Two names for materialise. Agent-verb leaf must pick.

4. **APM as mesh composition vs products uncoupled**  
   Early stack + “skill ships mesh via APM deps” vs `atlas-apm-uncoupled`. Compatible only if APM is *just files*. Incompatible if Atlas grows an APM client or APM grows Atlas hooks.

5. **Edit skill Atlas in place (works) vs APM cycle forbids it**  
   Successful today in the working tree; a published APM copy has no remote. Repair is Atlas CLI after copy, not changing APM.

6. **`--target-skill` into `references/atlas` vs “that folder is authored internal memory”**  
   Installing a third-party corpus into process memory fights the path signal.

7. **Worktree write vs submodule+PR write**  
   Early T2 vs later lean. Worktree should be marked alternative if we keep the PR path.

8. **Query-out-of-scope vs query as required agent verb**  
   Scope fence vs literacy list. Compatible if `query` is named, not designed, in this discussion.

9. **Git optional vs git is the overlay**  
   `git-aware-atlas` vs later “git is the overlay / no overlay.” A no-git Atlas is then a degraded reader, not a peer writer.
