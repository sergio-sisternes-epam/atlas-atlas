---
type: protostar
title: "SMR configuration with skill-owned SMO"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Forming declarative bridge between third-party schema semantics, optional skill presets and explicitly selected host recall policy."
status: open
kva: forming
growth: true
star_kind: refine
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/recall-architecture/contract-proposal.md
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/contract-proposal.md
    kind: derived_from
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: follows
---

## User direction

Semantic Memory Recall (SMR) is configurable Coarse, Rank and Retrieve.
Semantic Memory Organisation (SMO) belongs to third-party skills through
SCHEMA extensibility. Skills may offer SMR presets; the store owner explicitly
selects them. Preset installation is not activation.

## Candidate boundary

Skills own domain types, fields, lifecycle values, relationship meanings,
templates, folder conventions and authoring procedures. Atlas implements
portable format/storage invariants, schema-extension mechanics and generic
retrieval operators. OKF remains the minimal format authority; unknown page
types and metadata are not grounds for rejecting otherwise valid content.

SCHEMA extensions should expose declarative semantic bindings, not execution
hooks: searchable fields, typed facets, lifecycle selections and directed edge
fields, scoped to the contribution's applicable pages. The owning skill
defines what a value means; Atlas can execute explicit predicates without
hard-coding those meanings. A status exclusion is retrieval policy, not an
access-control mechanism.

Compile produces one effective schema/binding registry with contributor
identity and revision. Indexing and search consume that same validated
registry. A neutral projection retains page identity, text, arbitrary metadata
and typed edges instead of requiring KVA or a universal domain taxonomy.
Unbound content remains generically searchable; unsupported registered
capabilities in a selected profile cause an explicit diagnostic.

SMR profiles select stage drivers, compatible bindings, filters, ranking
weights, expansion rules and budgets. Coarse supplies candidate identities;
Rank orders them; Retrieve assembles bounded page evidence and optional graph
context without changing authored memory. FTS5 can fuse the first two stages.
Bindings and profile compatibility must prevent false-negative candidate cuts.

## Preset ownership and activation

Use contribution-qualified preset identities, such as `discuss:explore`.
Store-owner policy explicitly selects and optionally customises one.
No last-installed-wins merge and no implicit combination of domain semantics.
Tentative precedence: generic defaults, selected preset, host overrides,
allowed invocation overrides. Host-enforced safety limits remain ceilings;
profiles cannot bypass staging exclusion or driver trust boundaries.

Versioned portable profile intent belongs with store configuration. Machine
paths, binary locations, endpoints and credentials are local runtime settings,
not domain SMO. Declarative schema must not launch commands or install drivers.
Exact storage keys and CLI flags are unapproved interface sketches.

Fingerprint effective schema/bindings and index-relevant settings in caches.
Schema or indexed-field changes invalidate the relevant projection; changing
a query limit need not rebuild content. Removed preset dependencies must be
reported rather than silently selecting another skill's policy.

## Observed implementation gaps

- `core/overlay.py` protects core `query`, `compile`, `structure` and base
  domain types. It admits unique extra root keys, but two overlays cannot
  share one such key. A contributor-qualified registry requires deliberate
  composition semantics, not simply inserting one common `smr` key everywhere.
- `core/schema.py:load_schema` reads base SCHEMA only. Search uses this
  loader, so accepting extension JSON would not itself enable those bindings.
- `commands/search.py` contains fixed field tokens and KVA/exit-state handling.
  Those domain interpretations need schema-driven bindings for the proposed
  ownership boundary to be real.
- Reserved domain templates/types need an explicit compatibility migration
  towards a default contribution rather than permanent core ontology. Do not
  remove existing KVA behaviour or alter existing stores implicitly.

The historical `autogenesis/discuss/compile-type-contract/reusable-schema.md`
supports explicit schema evolution rather than silently editing sibling
stores. Its then-current CLI inventory is historical, not today's API.

## Accepted configuration format decision

The user asked whether a closed validation schema favours YAML or JSON.
The user accepted JSON as the sole configuration format initially, matching
SCHEMA.json and installed JSON overlays, with real, versioned JSON Schema
validation. The authoritative pin is
[decision-json-configuration.md](decision-json-configuration.md).
The wider binding and profile proposal remains forming. The current
`references/SCHEMA.contract.json` explicitly describes itself as a normative
field list rather than a full JSON Schema; it is not already that validator.

Closure is independent of serialisation. YAML can be validated after parsing
to the JSON data model, but requires a constrained loader and policy for tags,
aliases, merge keys, non-string keys and implicit scalar typing. JSON avoids
those additional rules; its parser must still reject duplicate keys and
non-standard numeric constants.

Close the Atlas-owned configuration envelope and driver option schemas.
Allow extensions only at registered contribution namespaces, and validate
each payload against its contribution-owned schema. With composed JSON Schema
definitions, use closure at the composed boundary (for example
unevaluatedProperties with a supported modern draft), not a blanket base
additionalProperties rule that blocks intended extensions.

Closed configuration does not close OKF page types or raw metadata. Unknown
configuration keys should fail explicitly; unknown valid page metadata remains
portable. Schema validation covers shape; capability compatibility and preset
references still need semantic validation. Do not add YAML/JSON dual-authoring
unless a demonstrated authoring need justifies it.

## Open refinement

Specify the contribution binding vocabulary, scoped validation rules, named
profile composition and backward-compatibility strategy in formal design.
Do not relax protected core keys wholesale. Prototype the boundary with two
different skill vocabularies using the same SMR drivers; changing drivers
should not require rewriting their pages or ontology.

This page is discussion memory, not a completed behavioural contract or
implementation authority.
