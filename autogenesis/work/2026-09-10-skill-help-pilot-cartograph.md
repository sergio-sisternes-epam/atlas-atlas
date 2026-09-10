---
type: decision
title: "Introduce Cartograph through sourced Atlas help and explicit Copilot activation"
created: 2026-09-10
work_id: 2026-09-10-skill-help-pilot
status: accepted
kva: alive
origin: derived
sensitivity: internal
description: "Current Cartograph package, connected knowledge stores, and the boundary between explanatory help and installation."
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot.md
    kind: implements
  - path: autogenesis/work/2026-09-10-skill-help-pilot-reference-gaps.md
    kind: follows
  - path: autogenesis/work/2026-09-10-skill-help-pilot-activation-cards.md
    kind: follows
  - path: decisions/cartograph-fork-in-atlas.md
    kind: supersedes
  - path: help/cartograph.md
    kind: related
  - path: help/open-cartograph.md
    kind: related
  - path: help/install-and-open-cartograph.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph-experience.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/decisions/cartograph-v030-interaction-contract.md
    kind: derived_from
  - path: atlas://atlas-cartograph-atlas/work/cartograph-v030-2026-09-10.md
    kind: derived_from
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/apm.yml
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/docs/usage.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph-atlas/blob/fd17c25c7bf4151e4e86960a987a605324a64901/work/cartograph-v030-2026-09-10.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph-atlas/blob/fd17c25c7bf4151e4e86960a987a605324a64901/decisions/cartograph-v030-interaction-contract.md
---

## Decision

Atlas help and getting-started should suggest **Cartograph** when a visual
explanation of knowledge pages, types and relationships would help the user.
Cartograph is the separately distributed `sergio-sisternes-epam/atlas-cartograph`
APM package, a knowledge-graph canvas for the **GitHub Copilot App**. The native
installation/opening guidance is Copilot-only; it is not a promise that every
Copilot client has a canvas host.

The proposed internal `visualise` path handles explicit open/install intent.
Explanatory help may link to its instructions but must not install a package,
grant executable trust, enable a feature, mount a store or start a collector.
The path is specified in the pilot plan; this memory does not make it part of
the installed skill registry or create an `atlas visualise` CLI command.

## Rationale

The user requested a Cartograph memory, a connection between the two Atlases,
help articles, an explicit install-and-open activation path, and instructions
for the Copilot **Canvas** menu. The viewer makes existing knowledge easier to
explore; it does not replace Atlas search or turn visual proximity into evidence.

The pinned package README and manifest establish the current distribution:
version 0.3.0, target `copilot`, self-contained runtime in
`.apm/extensions/cartograph/`, and no Atlas package dependency. The earlier
decision about `atlas/addons/cartograph/` and Grok Build is preserved as
historical guidance, not used for current Copilot setup.

The linked Cartograph interaction decision explains first selection for a
neighborhood, repeated selection for Markdown, visible search and independent
folder watching. Its delivery work records a previous successful release and
global deployment. That earlier success is evidence about that episode, not
proof that this session installed or tested a fresh package.

## Knowledge connection and ownership

| Knowledge home | Mount identity | Cartograph graph identity |
|---|---|---|
| Atlas concepts, onboarding and this pilot | `github.com/sergio-sisternes-epam/atlas-atlas` | `atlas-skill-memory` |
| Cartograph behavior and operational experience | `github.com/sergio-sisternes-epam/atlas-cartograph-atlas` | `atlas-cartograph-atlas` |

The graph identities are the existing `SCHEMA.json` `atlas_id` values; they
are not interchangeable with the host/org/repo identities accepted by Atlas
mount/resolve. No schema identifier is renamed for this connection.
The consumer mesh registers both stores at `main`, with Git submodules pinning
their consumed revisions. Atlas remains the explicit primary write-home.

Articles carry typed `derived_from` evidence edges and `related` navigation
edges using Cartograph's short graph-qualified URI syntax. The reciprocal
[Cartograph connection](atlas://atlas-cartograph-atlas/help/atlas-connection.md)
points back to Atlas-owned help rather than copying these memories.
Pinned HTTPS source URLs retain traceability independent of graph navigation.
An external URI is not an automatic mount, and Atlas compile alone does not
prove that a cross-store graph endpoint exists.

The [native opening experience](2026-09-10-skill-help-pilot-cartograph-experience.md)
records successful reciprocal resolution and an important compatibility limit:
Atlas CLI emits non-blocking unknown-dependency warnings for Cartograph's
short graph IDs despite both canonical stores being mounted. Use the identity
table above for CLI operations; do not interpret a successful graph link as
proof of a shared identifier contract across the tools.

## Activation and consent boundaries

Reuse an available running Cartograph extension. If installation is needed,
explain its project scope and ask for executable trust before modifying the
consumer manifest. For the sourced APM 0.30.0 procedure, enable only the
experimental `canvas` flag if disabled and grant only `canvas: true` to the
source repository key. Preserve existing manifest targets and permissions;
never silently widen scope to a global install or bypass an organization deny.
Reload extensions, discover the provider and capabilities, open the canvas,
and report failure honestly if it cannot show the requested stores.

Basic viewing and accessible-folder watching require no privileged collector.
Read-access highlighting is a separate, explicit macOS collector operation
with administrator and Full Disk Access requirements. Do not enable it as
part of onboarding, installing or opening.

For missing reference information, follow the reference-gap decision: query
relevant Atlas knowledge; if retrieval fails, clearly disclose limited help
and the unavailable store. Successful search without usable evidence is a
knowledge gap, not an outage. Cards identify the intent and only the Atlases
whose evidence actually contributed.

## Observed evidence and limits

On 2026-09-10 in project session 9d0a896f-fb3f-4f6d-a84e-8014e2ab4231:
Atlas search for `cartograph` exposed the older in-skill decision. Cartograph
Atlas search for `APM canvas install opening` found the delivery work and
interaction decision linked above. The package README, manifest, usage
instructions and release metadata were also read.

APM reported version 0.30.0 with `canvas` already enabled. Extension discovery
reported a running `user:cartograph`; capability discovery exposed automatic
multi-store opening, `get_state`, `reload` and explicit selection. These are
observations of this host, not universal prerequisites already met for users.
No installation, global configuration change or privileged capture was needed
to author these memories. Installation and failure scenarios remain unevaluated
here. Future pattern extraction still requires repeated implementation evidence.
