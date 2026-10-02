<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.131

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.131** was hardened automatically. 28 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): Multiple `${{ inputs.* }}` expressions are interpolated directly inside `run:` shell command strings in action.yml. This allows an attacker who controls those inputs to inject arbitrary shell commands.

In the 'Install release-plz' step:
  - `cargo-binstall release-plz@${{ inputs.version }}` — the version value is injected directly into the shell command without quoting or sanitization.

In the 'Run release-plz' step, all of the following are interpolated directly:
  - `if [[ -n "${{ inputs.config }}" ]]` and `CONFIG_PATH=("--config" "${{ inputs.config }}")`
  - `if [[ -n "${{ inputs.verbose }}" ]]`
  - `if [[ -n "${{ inputs.dry_run }}" ]]`
  - `if [[ -n "${{ inputs.token }}" ]]` and `TOKEN=("--token" "${{ inputs.token }}")`
  - `if [[ -n "${{ inputs.forge }}" ]]` and `FORGE=("--forge" "${{ inputs.forge }}")`
  - `if [[ -n "${{ inputs.backend }}" ]]` and `FORGE=("--forge" "${{ inputs.backend }}")`
  - `if [[ -n "${{ inputs.registry }}" ]]` and `ALT_REGISTRY=("--registry" "${{ inputs.registry }}")`
  - `if [[ -n "${{ inputs.manifest_path }}" ]]` and `MANIFEST_PATH=("--manifest-path" "${{ inputs.manifest_path }}")`
  - `if [[ -n "${{ inputs.project_manifest }}" ]]` and `MANIFEST_PATH=("--project-manifest" "${{ inputs.project_manifest }}")`
  - `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release-pr" ]]` (twice)
  - `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release" ]]` (twice)

All these must be moved to `env:` variables and referenced as quoted shell variables (e.g., `"$INPUT_CONFIG"`) to prevent injection.

Locations:

- `action.yml:79`
- `action.yml:88`

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

1. 'Install release-plz' step: Added env: block with INPUT_VERSION: ${{ inputs.version }} and replaced the inline ${{ inputs.version }} in the run: block with "${INPUT_VERSION}".

2. 'Run release-plz' step: Added env: block with 10 variables (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND) mapping all ${{ inputs.* }} expressions. Replaced all inline ${{ inputs.* }} references throughout the run: block with their corresponding $INPUT_* shell variable references.

All ${{ inputs.* }} expressions now appear only in env: blocks (safe assignments), not inside shell command strings.

