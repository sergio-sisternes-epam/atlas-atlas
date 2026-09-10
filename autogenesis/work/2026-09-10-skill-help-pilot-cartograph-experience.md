---
type: experience
title: "Connected Atlas help opened across two Cartograph knowledge stores"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: recorded
origin: internal
sensitivity: internal
description: "Observed native opening and reciprocal graph resolution, with an explicit CLI-versus-graph identity limitation."
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: records
  - path: autogenesis/work/2026-09-10-skill-help-pilot-experience.md
    kind: follows
  - path: help/cartograph.md
    kind: related
  - path: help/open-cartograph.md
    kind: related
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph-atlas/blob/fd17c25c7bf4151e4e86960a987a605324a64901/work/cartograph-v030-2026-09-10.md
---

## Context

The user requested concrete Cartograph memories, a connection between
`atlas-atlas` and `atlas-cartograph-atlas`, and Copilot-only help including
the Canvas menu and an explicit install/open activation path. The existing
help runtime pilot still awaited implementation approval.

## What happened

APM 0.30.0 already had the `canvas` flag enabled and the host already ran
`user:cartograph`. The package source and Cartograph Atlas supplied current
distribution and interaction evidence that the older Atlas Build-fork
decision did not contain. Its historical body was preserved with a successor
link rather than used as current installation advice.

The Cartograph knowledge repository was mounted at its canonical project
location alongside the existing, locally modified Atlas store. Its consumed
revision was `fd17c25c7bf4151e4e86960a987a605324a64901`; the original Atlas
revision was `a2877113d5e4423edfddc90363ea086d27bed4e6`. New help and memories
were local additions, not remotely published files.

The native `cartograph` canvas was opened without an explicit root. Its
initial post-authoring state reported `phase: map`, no error, both expected
store roots, 430 nodes and 2093 edges. These counts describe that snapshot,
not a fixed fixture or performance target. Explicit native selection succeeded
for the Atlas overview and the Cartograph reciprocal connection page.

The installed Cartograph parser's `loadCombinedGraphs` and
`loadPageFromRoots` were then exercised read-only. Both directions between
`atlas-skill-memory::help/cartograph` and
`atlas-cartograph-atlas::help/atlas-connection` resolved as explicit
`relates` edges with `relKind: related`; both graph-qualified page URIs
resolved. This checks actual graph endpoints, not merely string presence.

## Outcome

The two-store map and reciprocal knowledge connection worked in the existing
native installation. No APM installation, executable permission change,
feature enablement, global deployment, remote push or privileged collector
was performed. The collector remained `waiting`; the default highlight-enabled
setting alone does not mean collection is running.

Both Atlas compiles exited 0, but emitted non-blocking
`atlas_uri_unmounted` warnings for the graph-qualified links. This is a real
compatibility limit: the Atlas CLI interprets an `atlas://` pointer through
its host/org/repo normalizer, while this Cartograph version names the graph
using the short schema `atlas_id`. Consequently, these warnings do not mean
the two canonical repositories were absent. The native map and parser
confirmed they were present.

Do not hide this mismatch, add fabricated mesh entries, rename schemas, or
claim short graph URIs are portable CLI pointers. The articles give the full
mount IDs separately and preserve HTTPS source pins. Unifying link identity
across tools is follow-on design work, not silently included in this memory
task. This result supports linked visual help in this host, not a universal
cross-tool resolution claim.

Fresh-install, missing-host, denied-trust and retrieval-failure branches were
not executed. Nor was the proposed help/visualise runtime implemented, a human
visual acceptance obtained, or a reusable Autogenesis pattern admitted.
