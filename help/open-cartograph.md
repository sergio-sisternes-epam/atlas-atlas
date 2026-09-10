---
type: document
title: "Open Cartograph from the GitHub Copilot Canvas menu"
created: 2026-09-10
reviewed_at: 2026-09-10
subject: atlas
topic: cartograph-open
status: published
origin: derived
sensitivity: internal
description: "Open an existing Cartograph canvas without reinstalling it or enabling privileged activity capture."
applies_to:
  product: atlas-cartograph
  version: "0.3.0"
  harness: github-copilot-app
  source_revision: 41ca3e2a0c2918acaa57ce5ec898033d7a17b786
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: derived_from
  - path: help/cartograph.md
    kind: related
  - path: help/install-and-open-cartograph.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/help/atlas-connection.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/decisions/cartograph-v030-interaction-contract.md
    kind: derived_from
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/docs/usage.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
---

# Open your knowledge map

In your **GitHub Copilot App** project session, open the **Canvas** menu and
select **Cartograph**. If it is already open, select its panel. The menu
route is the user-facing entry requested for this help pilot; menu placement
and shortcuts vary by host version and are intentionally not assumed here.

You can also ask the agent, "Open Cartograph for this project's Atlases."
This is an explicit request to open a viewer, not permission to install a
missing package or start a privileged collector.

## Choose the right view

By default, the canvas opens all recognized Atlas stores below the current
workspace's `.atlas/`. No stores means a picker, not an automatic repository
mount. For the Atlas/Cartograph connection, both knowledge stores must be
available locally and included in the view. An explicit single-store root
overrides discovery and can therefore hide the other end of a link.

Project and user installations may coexist. Choose the provider you intend:
`project:cartograph` for the project deployment or `user:cartograph` for an
existing user deployment. Reuse the current installation; do not install a
second one just to open the map. The runtime's build badge identifies the
version and source when available.

The [pinned usage guide](https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/docs/usage.md)
is the source for discovery, explicit roots, providers and native workspace
resolution. The host must supply valid session workspace context. A failure
must not be hidden by opening the main checkout or the extension directory.

## If Cartograph is missing or fails to open

Ask the agent to reload extensions, then inspect whether Cartograph is
registered and running. A failed extension needs its actual error examined;
do not keep reinstalling without understanding it. If the package is absent,
use [Install and open Cartograph](install-and-open-cartograph.md).

If this Copilot client has no canvas host, this native path is unavailable.
State that limitation rather than inventing a settings switch or claiming
that another Copilot product supports it. Package errors and knowledge-query
failures are different: inability to open the viewer does not by itself mean
Atlas search is unavailable.

## Agent opening procedure

Discover extensions and the declared `cartograph` canvas capabilities. Use
`list_canvas_capabilities` before `open_canvas`, choose a fresh panel
`instanceId`, and supply `extensionId` when providers need disambiguation.
Omit `root` when the user wants all locally mounted Atlases. Use `get_state`
after opening to confirm the requested stores and surface any error. A
registered extension alone does not prove the graph opened.

For a help question, keep the activation intent as help and report only the
Atlases whose evidence contributed. Switch to the proposed `visualise`
operation only on explicit action intent; it is not yet a released Atlas
skill path. Do not advertise an `atlas visualise` shell command.

Basic viewing needs no administrator access. Leave read-access monitoring
off unless the user separately requests it and authorizes its requirements.
