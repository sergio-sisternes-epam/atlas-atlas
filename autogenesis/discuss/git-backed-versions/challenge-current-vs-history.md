---
type: experience
title: "Think-challenge — current state vs full history (keep tip vs prune+ref)"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: probed
kva: forming
reality: current
description: "Grounded counters to the keep-all-on-tip vs terminate-and-git-ref choice for evolving memories (e.g. SSH key lineage). Search-backed challenge, not invent."
tags: [think-challenge, claim-a, claim-b, probe]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: counters
  - path: autogenesis/discuss/git-backed-versions/pin-single-summary-stand-in.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: related
---

## Context

User framing (2026-09-27): evolving facts (SSH keys) need both a handy current memory and a trail of what/when/why. Two options — (1) keep all memories live on tip near the index, including superseded; (2) terminate/delete with git `ref` pointers for costly history. Think-challenge grounded in search.

## What happened

### Counters (search-backed)

1. **Physical delete is the risky half of option 2.** KCS prefers archive (remove from default search, keep record and links) over delete; delete breaks incident links. Seriousness: high for prune-without-stub mistakes. Sources: KCS Technique 5.2; HelpSite content-debt guidance.

2. **Aggressive archive/prune can hurt completeness.** KCS 5.5: archiving often treats findability symptoms; over-reducing the collection compromises rare-but-valuable knowledge. Seriousness: medium-high against “always drop whole failed path.”

3. **Keeping everything visible on tip is also a failure mode.** Stale-but-searchable articles cause wrong actions (content debt). Archive/hide from default retrieval is required even if bytes stay. Seriousness: high against naive option 1. Source: HelpSite; KB deprecation guides.

4. **History without a maintained current projection is expensive.** Event-sourcing practice: reconstituting “now” from the log is the costly read; you need a deliberate tip/read model. Seriousness: high against “git alone is enough for current state.” Sources: CQRS/ES trade-off writeups (Palma; Voramongkol; Qamar).

5. **Retired without a why-pointer is a known standards failure.** IESG: Historic RFCs long lacked a pointer from the retired doc to *why*; status-change docs fixed that. Obsoletes ≠ Historic. Seriousness: high support for summary+why stand-in; warns against SHA-only tombs. Source: IESG Historic statements.

6. **Temporal queries need commit-scoped soft-delete metadata.** Soft-delete that only stamps wall-clock time breaks as-of history walks; `last_seen_commit` (or equivalent `ref`) is load-bearing. Seriousness: medium for Atlas `ref` design. Source: codeindex temporal handoff notes.

### Outcome of probe

The dual need (handy current + recoverable why) stands. Neither “keep all live and searchable” nor “delete and hope git is enough” survives alone. Hardening points toward: tip holds the current projection + thin why-stand-ins; default search excludes terminated; history via `ref`/archive; do not equate supersede with terminate.

## Outcome

Probe did not kill the dual-need thesis. It kills naive option 1 (visible tip clutter) and naive option 2 (delete without searchable exclusion discipline and without why on tip).
