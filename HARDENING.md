<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.131

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.131** was hardened automatically. 29 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### script-injection (severity: high)

The 'Install release-plz' run: step directly interpolates ${{ inputs.version }} into a shell command string (sub-rule a). A caller can supply a version string containing shell metacharacters (e.g. semicolons, backticks, $(...)) that execute before any quoting takes effect. Offending line: `release-plz@${{ inputs.version }}`

Locations:

- `action.yml:80`

### script-injection (severity: high)

The 'Run release-plz' run: step directly interpolates multiple ${{ inputs.* }} expressions into shell command strings (sub-rule a). Affected inputs include inputs.config, inputs.verbose, inputs.dry_run, inputs.token, inputs.forge, inputs.backend, inputs.registry, inputs.manifest_path, inputs.project_manifest, and inputs.command. Each is interpolated directly into shell conditionals (e.g. `if [[ -n "${{ inputs.config }}" ]]`) and array assignments (e.g. `CONFIG_PATH=("--config" "${{ inputs.config }}")`). A calling workflow can supply attacker-controlled values containing shell metacharacters that execute before any quoting takes effect.

Locations:

- `action.yml:88`
- `action.yml:89`
- `action.yml:91`
- `action.yml:92`
- `action.yml:97`
- `action.yml:103`
- `action.yml:104`
- `action.yml:109`
- `action.yml:110`
- `action.yml:115`
- `action.yml:116`
- `action.yml:117`
- `action.yml:122`
- `action.yml:123`
- `action.yml:128`
- `action.yml:129`
- `action.yml:134`
- `action.yml:135`
- `action.yml:140`
- `action.yml:141`

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

1. 'Install release-plz' step: Moved ${{ inputs.version }} to an env: block as INPUT_VERSION, and updated the cargo-binstall command to use "release-plz@${INPUT_VERSION}" instead of the direct expression interpolation.

2. 'Run release-plz' step: Moved all 10 ${{ inputs.* }} expressions (config, verbose, dry_run, token, forge, backend, registry, manifest_path, project_manifest, command) to an env: block with INPUT_* variable names. Updated all 20+ references throughout the shell script to use the corresponding environment variables ($INPUT_CONFIG, $INPUT_VERBOSE, etc.) instead of direct ${{ }} expression interpolation. All remaining ${{ inputs.* }} occurrences are now exclusively in env: blocks, which is the safe pattern.

### Iteration 2

**Fixes applied:** script-injection

**Notes:**

Moved `${{ secrets.GITHUB_TOKEN }}` from the `run:` shell command string into an `env:` block as `GH_TOKEN` in the 'Update major tag' step of `.github/workflows/update_main_version.yml`. The shell command now references `${GH_TOKEN}` as a plain environment variable instead of having the token value interpolated directly via YAML template expansion.

