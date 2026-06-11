<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.130

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **release-plz--action/v0.5.130** was hardened automatically. 28 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Two `run:` steps in action.yml directly interpolate `${{ inputs.* }}` expressions into shell command strings (rule a), allowing an attacker who controls input values to inject arbitrary shell commands.

**Step: "Install release-plz"** — `inputs.version` is interpolated directly into the cargo-binstall command:
```
cargo-binstall \
    release-plz@${{ inputs.version }}\
```

**Step: "Run release-plz"** — Multiple inputs are interpolated directly into shell conditionals and array assignments:
- `if [[ -n "${{ inputs.config }}" ]]` and `CONFIG_PATH=("--config" "${{ inputs.config }}")`
- `if [[ -n "${{ inputs.verbose }}" ]]`
- `if [[ -n "${{ inputs.dry_run }}" ]]`
- `if [[ -n "${{ inputs.token }}" ]]` and `TOKEN=("--token" "${{ inputs.token }}")`
- `if [[ -n "${{ inputs.forge }}" ]]` and `FORGE=("--forge" "${{ inputs.forge }}")`
- `if [[ -n "${{ inputs.backend }}" ]]` and `FORGE=("--forge" "${{ inputs.backend }}")`
- `if [[ -n "${{ inputs.registry }}" ]]` and `ALT_REGISTRY=("--registry" "${{ inputs.registry }}")`
- `if [[ -n "${{ inputs.manifest_path }}" ]]` and `MANIFEST_PATH=("--manifest-path" "${{ inputs.manifest_path }}")`
- `if [[ -n "${{ inputs.project_manifest }}" ]]` and `MANIFEST_PATH=("--project-manifest" "${{ inputs.project_manifest }}")`
- `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release-pr" ]]`
- `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release" ]]`

All these values should be passed via `env:` variables and referenced as `"$VAR"` in the shell script instead.

Locations:

- `action.yml:82`
- `action.yml:89`

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

Fixed all script injection findings in actions/hardened/release-plz--action/v0.5.130/action.yml:

1. **"Install release-plz" step**: Moved `${{ inputs.version }}` to an `env:` block as `RELEASE_PLZ_VERSION`, and updated the run script to use `${RELEASE_PLZ_VERSION}` instead.

2. **"Run release-plz" step**: Moved all 10 `${{ inputs.* }}` expressions to an `env:` block (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND), and updated all references in the shell script to use the corresponding `$INPUT_*` environment variables instead of inline `${{ }}` expressions.

