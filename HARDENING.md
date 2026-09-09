<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.134

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.134** was hardened automatically. 29 finding(s) were identified and resolved across 3 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' run: block in action.yml directly interpolates `${{ inputs.version }}` inside a shell command string: `cargo-binstall release-plz@${{ inputs.version }}`. An attacker-controlled version string (e.g. containing `;`, `|`, `$(...)`, or newlines) is expanded by the YAML template engine before the shell ever sees it, enabling arbitrary command injection. The value must be passed via an env: variable and properly quoted instead.

Locations:

- `action.yml:88`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' run: block in action.yml directly interpolates multiple `${{ inputs.* }}` expressions inside shell command strings, including: `${{ inputs.config }}`, `${{ inputs.verbose }}`, `${{ inputs.dry_run }}`, `${{ inputs.token }}`, `${{ inputs.forge }}`, `${{ inputs.backend }}`, `${{ inputs.registry }}`, `${{ inputs.manifest_path }}`, `${{ inputs.project_manifest }}`, and `${{ inputs.command }}`. These appear in [[ ]] conditional tests, echo statements, and array assignments. Because YAML template substitution occurs before the shell parses the script, any of these inputs containing shell metacharacters (`;`, `|`, `$(...)`, backticks, newlines, etc.) enables arbitrary command injection. All inputs must be routed through env: variables and properly double-quoted in the shell script.

Locations:

- `action.yml:96`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.version }}" appears directly in run: block of step "Install release-plz"; move to env: map

Locations:

- `action.yml:89`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:99`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:101`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:103`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.verbose }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:108`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.dry_run }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:115`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.token }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:122`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.token }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:125`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:130`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:132`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:133`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:134`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:137`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:138`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.registry }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:143`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.registry }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:145`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.registry }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:146`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.manifest_path }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:151`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.manifest_path }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:153`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.manifest_path }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:154`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.project_manifest }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:155`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.project_manifest }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:157`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.project_manifest }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:158`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.command }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:163`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.command }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:163`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.command }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:190`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.command }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:190`

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection, static-inline-injection

**Notes:**

Fixed all script injection findings in hardened/action/action.yml:
1. 'Install release-plz' step: moved `${{ inputs.version }}` to an `env:` block as `INPUT_VERSION` and replaced the inline interpolation with `"${INPUT_VERSION}"` in the shell command.
2. 'Run release-plz' step: moved all 10 `${{ inputs.* }}` expressions (config, verbose, dry_run, token, forge, backend, registry, manifest_path, project_manifest, command) to an `env:` block as `INPUT_CONFIG`, `INPUT_VERBOSE`, `INPUT_DRY_RUN`, `INPUT_TOKEN`, `INPUT_FORGE`, `INPUT_BACKEND`, `INPUT_REGISTRY`, `INPUT_MANIFEST_PATH`, `INPUT_PROJECT_MANIFEST`, and `INPUT_COMMAND` respectively. All occurrences in the shell script body were replaced with properly double-quoted `"$INPUT_*"` references. No `${{ inputs.* }}` expressions remain in any `run:` block.

### Iteration 2

**Fixes applied:** script-injection

**Notes:**

Fixed script-injection in .github/workflows/update_main_version.yml line 20. Moved `${{ secrets.GITHUB_TOKEN }}` out of the run: shell command and into an env: block as `GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}`. Updated the git remote set-url command to reference `${GH_TOKEN}` as an environment variable instead of directly interpolating the expression.

### Iteration 1

**Fixes applied:** script-injection

**Notes:**

Fixed script injection vulnerability in `.github/workflows/update_main_version.yml` by double-quoting `$TAG_NAME` in two `echo` command substitutions (lines 26 and 28). Changed `echo $TAG_NAME` to `echo "$TAG_NAME"` in both the VERSION_MAJOR and VERSION_MINOR assignments. This prevents shell metacharacter injection via a crafted tag name derived from the workflow-controllable `${GITHUB_REF##refs/tags/}` environment variable.

