<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.129

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.129** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' run: step directly interpolates `${{ inputs.version }}` into a shell command string (`cargo-binstall release-plz@${{ inputs.version }}`). A calling workflow can supply a crafted version string containing shell metacharacters (e.g. `;`, `$(...)`, `|`) that will be executed by the shell before any quoting takes effect. The value must be moved to an env: variable and that variable must be double-quoted in the shell command.

Locations:

- `action.yml:84`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' run: step directly interpolates multiple `${{ inputs.* }}` expressions into shell command strings and conditionals. Every one of the following inputs is expanded by the GitHub Actions template engine before the shell sees the script, allowing an attacker-controlled calling workflow to inject arbitrary shell commands via shell metacharacters: `inputs.config` (used in `if [[ -n "${{ inputs.config }}" ]]`, `echo "using config from '${{ inputs.config }}'"`, and `CONFIG_PATH=("--config" "${{ inputs.config }}")`), `inputs.verbose`, `inputs.dry_run`, `inputs.token` (used in `TOKEN=("--token" "${{ inputs.token }}")`), `inputs.forge` (used in `FORGE=("--forge" "${{ inputs.forge }}")`), `inputs.backend` (used in `FORGE=("--forge" "${{ inputs.backend }}")`), `inputs.registry` (used in `ALT_REGISTRY=("--registry" "${{ inputs.registry }}")`), `inputs.manifest_path` (used in `MANIFEST_PATH=("--manifest-path" "${{ inputs.manifest_path }}")`), `inputs.project_manifest` (used in `MANIFEST_PATH=("--project-manifest" "${{ inputs.project_manifest }}")`), and `inputs.command` (used in `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release-pr" ]]` and the analogous `release` check). All of these must be moved to env: variables and referenced as double-quoted shell variables (`"$VAR"`) instead.

Locations:

- `action.yml:91`
- `action.yml:93`
- `action.yml:95`
- `action.yml:99`
- `action.yml:105`
- `action.yml:111`
- `action.yml:113`
- `action.yml:117`
- `action.yml:119`
- `action.yml:120`
- `action.yml:123`
- `action.yml:130`
- `action.yml:132`
- `action.yml:137`
- `action.yml:139`
- `action.yml:140`
- `action.yml:142`
- `action.yml:148`
- `action.yml:172`

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

- `action.yml:205`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.command }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:205`

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection, static-inline-injection

**Notes:**

Fixed all script injection findings in hardened/action/action.yml:

1. 'Install release-plz' step: Added `env: INPUT_VERSION: ${{ inputs.version }}` and changed `cargo-binstall release-plz@${{ inputs.version }}` to `cargo-binstall "release-plz@${INPUT_VERSION}"`.

2. 'Run release-plz' step: Added an `env:` block with 10 variables (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND) mapping each `${{ inputs.* }}` expression. Replaced all inline `${{ inputs.* }}` references throughout the shell script with the corresponding `$INPUT_*` environment variable references. All ${{ }} expressions now appear only in env: map assignments, not in run: shell strings.

