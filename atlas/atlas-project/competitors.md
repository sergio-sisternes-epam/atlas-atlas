---
type: document
title: "Competitor and neighbour catalogue (correct frame)"
created: 2026-08-27
description: "Named tools under the correct comparison classes. Not a Mem0-style leaderboard."
origin: derived
sensitivity: internal
status: alive
kva: alive
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/comparison-correct.md
    kind: derived_from
  - path: atlas-project/vision.md
    kind: related
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
---

## Content

Use this list when someone asks “what is Atlas like?” Point at the class first, then the name.

| Class | Examples | Steal | Refuse |
|---|---|---|---|
| InnerSource | InnerSource Commons patterns; GitHub InnerSource programs; Trusted Committers | Contribution guides, default-readable repos, PR as institutional act | Treating only *code* as InnerSource |
| Docs-as-code | Mintlify, Docusaurus | CI on docs PRs, same review as code | Becoming a docs theme |
| Spec-driven development | GitHub Spec Kit 1.0, Kiro, BMAD; forming: OpenSpec, GSD, Spec Kitty | Hold specify/plan/tasks as `document`s under a work hub | Replacing Atlas with another `/specify` CLI |
| Decision records | ADR folders, RFCs | `decision` + `supersedes` | Isolated ADR folders with no mesh |
| Work graphs | Beads (`relates_to`, `supersedes`, `ready`) | Work-queue UX later | Replacing pages with a Dolt issue DB |
| File wikis agents can edit | Basic Memory, ByteRover, DiffMem, LLM-wiki | MCP, hierarchical curation, git-as-time | Losing compile and work hubs |
| Catalogs | Backstage | System inventory as `document` mounts | Catalog-only mental model |
| Requirements suites | Jira, ADO Boards, Jama, DOORS | Lifecycle language for `work` status | SoR living only in the suite |
| Enterprise retrieval | Foundry IQ, Azure AI Search, Fabric IQ | Permissioned read of *merged* Atlas | Birthplace of claims |
| SCM at agent scale | GitHub, GitLab next-gen SCM, Cursor Origin | Provenance of agent writes, branch flood | Replacing git identity |

File-wiki peers (Basic Memory, ByteRover, DiffMem) are the nearest *storage* cousins. They still fail the multi-team PR + compile + work-hub test that Atlas is building.

Agent-memory SaaS names belong only on the terminated branch.

Landscape 2026-08-27: partners live under `partners/`. Forming SDD names under `landscape/`. Spec Kit reached 1.0.0 (2026-08-21). Foundry IQ knowledge bases GA; Search remains the index plane.

## Provenance

Vision scan 2026-08-27 plus landscape path first run same day. Wrong-frame notes stay in `wrong-path-agent-memory-layer/scan-2026.md`.
