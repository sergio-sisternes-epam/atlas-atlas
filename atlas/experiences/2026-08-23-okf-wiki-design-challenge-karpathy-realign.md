---
type: experience
title: "2026-08-23 design challenge: okf-wiki vs pure OKF / Karpathy — compile failure and realignment"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Session diagnosis that compile is broken (pointer-memory + ceremony), agents fall back to grep; comparison to public OKF; challenge that modular composition was the right aim but the heavy path was wrong; emerging direction toward minimal OKF surface + smallest possible compilation + composition."
tags: "[memory, design, challenge, okf, karpathy, compile, composition, work_id]"
origin: internal
sensitivity: internal
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: experiences/2026-08-23-atlas-design-plan.md
    kind: related
  - path: decisions/type-vocabulary.md
    kind: related
---
# 2026-08-23 design challenge: okf-wiki realignment

## Context

Ongoing Autogenesis design path (work_id `okf-wiki-karpathy-realign-simplify-compose-migrate-v1`, change-class new-surface) with objectives:

1. Reconsider structure vs original Karpathy LLM-wiki gist (raw + compile vs direct folders + connections).
2. Simplify query discipline for minimal/fast path while respecting okf.
3. Make knowledge modules + composition first-class so users can compound wiki knowledge.
4. Design migration discipline to any new agreed folder structure.

Cross-cutting constraint: skills ship as APM packages → no phone-home telemetry; all quality/usage ledgers must stay local.

## Diagnosis that triggered the deep challenge

User reported that the “compile” process is not working well. Agents fall back to unbounded grep. Quality snapshot on the meta-wiki itself still shows stubs, inventory digests, core_digest_only, and stale_compiled pages under E1. This is the same failure class first named a blocker on 2026-08-16 (pointer-memory).

Root causes identified:

- Structure is easy; semantic compile is hard. Gates mostly reward file-graph health.
- OKF + type vocabulary + progressive disclosure + activation cards + type-normalise gates create high process load. Models optimise for green gates instead of writing claim-bearing knowledge.
- Hybrid query + gaps was a correct reaction to unbounded grep, but treats the symptom while the compiled layer remains untrustworthy.

## Comparison performed

### Karpathy LLM Wiki (original)
- raw/ immutable sources → LLM compiles persistent interlinked wiki/.
- Query the compiled wiki.
- SCHEMA/operating contract is lightweight.
- Success = can the agent answer ordinary questions from the wiki without falling back to raw.

### Pure / public Open Knowledge Format (Google Cloud, v0.1 → v0.2)
- Directory of Markdown + YAML frontmatter.
- **Only hard requirement: non-empty `type` field.**
- Directory structure free.
- Reserved: `index.md` (progressive disclosure), `log.md` (history).
- Consumers must tolerate unknown types and unknown frontmatter keys.
- Practical tools (Google reference agent, openknowledge.sh, okfcli, Obsidian plugins, starters) stay thin: write good concepts, keep indexes useful, validate the tiny bar.
- Modular hierarchical composition is already native via ordinary folders + `index.md` + Markdown links. No promote ceremony required.

### Our okf-wiki implementation
- Added dual-axis ingest, pointer-memory completion contract, recommended type vocabulary + origin/sensitivity, E0–E3 quality efforts, hybrid L0/L1/L2 query + mandatory gaps/relevance, type-normalise gates, activation cards, substrate contracts, promote-to-module, mesh composition axes, etc.
- Local `okf` skill correctly stays close to the public minimal bar; okf-wiki layered a heavy operational system on top.

## Gaps we created
- Structure over substance (gates certify structure, not answerability).
- Compile is optional in practice (contracts exist on paper; runtime still accepts pointer-memory).
- Process load displaced content work.
- Query complexity treated the symptom.
- Over-constrained what “OKF-compliant” means operationally.
- Success metrics drifted from “does it answer?” to “do the structural gates pass?”.

## Challenge exchange

User agreed with the over-engineering diagnosis but clarified the original aim:

> The aim of okf-wiki was to produce an implementation of the standard that could support modular knowledge composition and compilation (what was wrongly named “ingestion”). What I did was create the next step in the journey, but I took the right direction.

Counter returned (and accepted in spirit by the user):

- Modular composition is already native to public OKF via free directories + index.md progressive disclosure + ordinary links. We did not need a parallel heavyweight system (promote, earned modules with special nested index rules, etc.).
- Compilation was the right goal; the machinery built for it is what broke the models.
- A “next step” that adds composition on top of a still-broken compile step is not progress.
- The legitimate next step is: take the public OKF minimal surface and add the *smallest* possible mechanisms that deliver reliable claim-bearing compilation + modular composition that agents can actually execute without falling back to grep.

User response: “I like your idea.” Requested that the discussion be stored as long-term memory.

## Emerging direction (not yet pinned or approved)

- Move toward public OKF minimalism on the compile and query surfaces.
- Keep the legitimate aims: durable compilation and modular composition.
- Cut or make strictly optional the ceremony that currently prevents models from producing usable knowledge.
- Simplified query stays pure L0 → L1 first; whole-tree/raw grep remains forbidden.
- Any enrichment for non-related ideas belongs to mesh / explicit explore / housekeep, not core query.
- Migration discipline must include answerability smoke, not only structural gates.
- Local-only telemetry remains mandatory (APM packaging constraint).

## Related existing memory

- [[raw/experiences/2026-08-16-skill-feedback-pointer-memory]]
- [[raw/experiences/2026-08-16-apm-ingest-pointer-memory]]
- [[learning-2026-08-16-pointer-memory-blocker]]
- [[learning-coverage-not-answerability]]
- [[decision-pointer-memory-completion-contract]]
- [[decision-hybrid-query-and-gaps]]
- [[decision-flat-knowledge-earned-modules]]
- [[decision-module-progressive-disclosure]]
- [[composition-axis-pins]]

## Explicit deferral

Knowledge-page creation / dual-axis ingest / formal pinning of the new direction is deferred to a later wiki-ingest or design-approval step. This remember only captures the session diagnosis and challenge outcome.

## Status

Design path still open (stops for approval). No product files beyond this experience and telemetry were written in this turn.

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **related:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **related:** [type-vocabulary](../decisions/type-vocabulary.md)
