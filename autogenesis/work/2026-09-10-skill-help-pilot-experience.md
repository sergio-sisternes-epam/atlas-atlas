---
type: experience
title: "Conversational Atlas help pilot and formal design capture"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: recorded
stage: design
origin: user
sensitivity: internal
plan_path: autogenesis/plans/2026-09-10-skill-help-pilot.md
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: records
  - path: autogenesis/work/2026-09-10-skill-help-pilot-proposal.md
    kind: derived_from
---

## Context

The user asked to explore getting-started and CLI-like help activation paths,
with pre-built references pinned as Atlas sources and enrichment from relevant
Atlases. The session ran in the Atlas repository. The user chose Atlas-first
scope and a bundled baseline that remains usable without a mounted store.

Source: user conversation on 2026-09-10 in project session
9d0a896f-fb3f-4f6d-a84e-8014e2ab4231. This is a curated event record, not a raw
transcript or fabricated benchmark. Product source was
3818586da56331949b03fe746ef21693d3c84169; the subject store began at
a2877113d5e4423edfddc90363ea086d27bed4e6.

## What happened

| User request | Observed response or feedback |
|---|---|
| Help intent without a clear path | Assistant proposed a complete version-qualified path overview instead of requiring a target |
| "I am new to Atlas. How it works?" | Assistant explained durable Git-backed Markdown knowledge and a first-use journey |
| "I want to understand how mount works" | Assistant explained local mounts, submodules and separate remote storage without running mount in that help turn |
| "Where can I store my atlas?" | Assistant favoured a dedicated repository and omitted an existing repository branch |
| Storage correction | User called the answer good but required both repository choices, treating the choice as preference |
| atlas-help schema and wiki idea | User proposed curated help pages built from learning and connected to wider knowledge |
| Linking articles to knowledge | Assistant proposed authoritative relates_to edges, precise body citations and external source references |
| Formalise and capture | User requested a formal work record and durable learning for future pattern extraction |

The earlier Autogenesis setup had already mounted the subject store for memory
capture. Thus this conversation does NOT prove that an implemented help path
works offline or performs zero writes. The simulated help turns explained
operations; surrounding authoring turns wrote discussion memory.

During formal design, a targeted search exposed a dated page still marked
alive that says init and schema do not exist. The loaded installed Atlas
registry contradicts that claim. The installed registry also differs from the
checkout's newer configure surface. These are concrete source-selection risks.

## Outcome

Persisted a proposed new-surface design with explicit pins, internal-source
challenge, deterministic-first probes, full scenario drafts and an approval
stop. Confirmed user decisions and observed lessons are separate records.
Retained a forming extraction candidate with an evidence bar.

No help paths, wiki articles, overlay, eligibility implementation or product
release were delivered. No claim of repeated use, measured quality delta,
construct success, external review or active pattern is justified.

deferred: agent-spec is not available in this session; preserve contract families and deterministic evaluation requirements in the plan

deferred: construct execution requires approved implementation; only scenario drafts and evaluation mapping exist

## Changed files

All paths below are relative to the resolved subject Atlas. No product files
were changed in formal design. This list covers the session's memory artifacts,
including the pre-design discussion record.

- autogenesis/index.md
- autogenesis/plans/index.md
- autogenesis/plans/2026-09-10-skill-help-pilot.md
- autogenesis/work/index.md
- autogenesis/work/2026-09-10-skill-help-pilot.md
- autogenesis/work/2026-09-10-skill-help-pilot-proposal.md
- autogenesis/work/2026-09-10-skill-help-pilot-experience.md
- autogenesis/work/2026-09-10-skill-help-pilot-decisions.md
- autogenesis/work/2026-09-10-skill-help-pilot-lessons.md
- log.md

The initial mount briefly changed the consumer mesh ref from main to HEAD.
That incidental change was restored; the final consumer configuration is
unchanged. Memory remains local in the mounted store until separately committed
and published; no remote publication is claimed.

## Follow-ups

Review the design before implementation. Collect actual with/without evidence
and repeated uses before extraction. Keep unrelated whole-store Discuss lint
findings outside this pilot; they were reported earlier, not resolved here.
