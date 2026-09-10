---
type: document
title: "Install and open Cartograph with APM in GitHub Copilot"
created: 2026-09-10
reviewed_at: 2026-09-10
subject: atlas
topic: cartograph-install-and-open
status: published
origin: derived
sensitivity: internal
description: "Scoped, consent-based setup: canvas flag, narrow package trust, pinned APM install and native opening."
applies_to:
  product: atlas-cartograph
  version: "0.3.0"
  apm_version: "0.30.0"
  harness: github-copilot-app
  source_revision: 41ca3e2a0c2918acaa57ce5ec898033d7a17b786
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: derived_from
  - path: autogenesis/plans/2026-09-10-skill-help-pilot.md
    kind: related
  - path: help/open-cartograph.md
    kind: related
  - path: help/cartograph.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/work/cartograph-v030-2026-09-10.md
    kind: derived_from
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/apm.yml
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/releases/tag/v0.3.0
  - https://github.com/sergio-sisternes-epam/atlas-cartograph-atlas/blob/fd17c25c7bf4151e4e86960a987a605324a64901/work/cartograph-v030-2026-09-10.md
---

# Install only when you need to

If Cartograph is already available, [open the existing canvas](open-cartograph.md).
Do not reinstall it or change global settings just to display an Atlas.

This guide is for **GitHub Copilot App with canvas support**. The package's
instructions were validated by its maintainers with **APM 0.30.0** and require
**Node.js 22 or later**, repository access and a compatible canvas host.
Recheck the current package instructions for other versions. A Copilot name
alone does not establish canvas support.

Cartograph executes extension code. Review and trust the package before
installing. Project installation is the scoped starting point here; a global
installation affects every Copilot session and requires a separate explicit
scope decision. This help page itself authorizes neither.

## 1. Inspect prerequisites and scope

From the consuming project, inspect:

```sh
apm --version
node --version
apm experimental list --json
```

If APM is absent, stop and follow its supported installation instructions;
do not download and execute an unreviewed bootstrap script. If there is no
`apm.yml`, explicitly initialize the intended project with APM before
continuing. Preserve existing dependencies, executable permissions and target
settings. If the selected install would remove another configured target,
resolve that conflict before applying it.

## 2. Grant only the required executable permission

After the user approves trusting this package, merge this entry into the
project's existing `apm.yml`; do not replace the rest of the manifest:

```yaml
executables:
  allow:
    sergio-sisternes-epam/atlas-cartograph:
      canvas: true
```

The [pinned package instructions](https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md#install-with-apm)
specifically warn that APM 0.30.0 checks the source dependency reference,
whereas `apm approve` can record a different package identity. The explicit
repository-key, canvas-only grant avoids approving unrelated executable types.
Do not use broad trust, `--force`, or a personal/global grant to bypass a
project or organization denial.

## 3. Enable the canvas feature only if disabled

With permission to change this APM setting, run this only when the prerequisite
inspection shows the `canvas` flag is disabled:

```sh
apm experimental enable canvas
```

This is an APM experimental feature, not a guessed Copilot UI setting.
Do not enable `copilot-app` workflow deployment, `copilot-cowork`, or unrelated
experimental features. In the authoring session the canvas flag was already
enabled, so this command was not needed or executed.

## 4. Install the pinned package

After approving the project scope and permission changes:

```sh
apm install sergio-sisternes-epam/atlas-cartograph#v0.3.0 --target copilot
```

The published `v0.3.0` release points to source commit
`fe6de71e56422bda09dd0a92cf59d683d883e396`. A full HTTPS Git source can be
selected explicitly if an APM default registry changes shorthand resolution;
do not silently substitute another package source. Preserve existing target
configuration rather than treating `--target copilot` as permission to remove
other targets.

APM deploys the complete runtime to `.github/extensions/cartograph/`. No
`npm install`, development shim copy, or consumer `src/` directory is needed.
Atlas repositories under `.atlas/` are input data, not extension imports.
Install success is not yet proof that the host loaded the canvas.

If installation is blocked, fails, or does not deploy the canvas, stop and
report the known cause. Do not silently fall back to a global install, another
ref, a trust bypass or repeated reinstall attempts. Leave unrelated user
settings untouched and describe any partial changes.

## 5. Reload and open

Reload extensions in the Copilot session. Open the **Canvas** menu and select
**Cartograph**, or ask the agent to discover the loaded provider and open it.
When both user and project copies exist, explicitly select the intended one.
Confirm the graph opens the requested Atlas stores; omit an explicit root to
discover all recognized stores in this workspace's `.atlas/`.

With no local stores, the picker is expected. Installation does not mount an
Atlas or authorize fetching one. Opening also does not start read-access
monitoring: privileged macOS capture is a separate opt-in operation, not a
setup prerequisite.

## Proposed activation path

The pilot calls the explicit operation **`visualise`**:
`references/paths/visualise.md` is its proposed skill module, not a shell
command. An intent such as "Install Cartograph for this project and open it"
selects this operation; "What is Cartograph?" stays explanatory help.

The activation card must expose intent, harness, selected provider, approved
installation scope, selected Atlas context and the Atlases actually used as
answer evidence. The execution branches are: reuse an available extension;
otherwise get the scoped trust/configuration approval and perform steps 1-5;
or report a concrete blocker. Agent execution must load the APM skill and
discover live canvas capabilities rather than guess commands or tool schemas.

This is a documented procedure and activation design. Runtime routing remains
pending approval of the [pilot plan](../autogenesis/plans/2026-09-10-skill-help-pilot.md).
The authoring session did not perform a fresh installation or test denied
trust, missing tools, failed downloads or unsupported hosts. Earlier release
and installation evidence belongs to the linked Cartograph delivery work.
