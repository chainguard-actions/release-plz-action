<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.135

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.135** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' step directly interpolates `${{ inputs.version }}` into a `run:` shell command: `release-plz@${{ inputs.version }}`. GitHub Actions performs template substitution before the shell parses the string, so a caller-controlled `version` input containing shell metacharacters (e.g. `;`, `|`, `$(...)`) can inject arbitrary commands. The value must be passed via an `env:` variable and then double-quoted in the shell script instead.

Locations:

- `action.yml:88`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' step directly interpolates multiple `${{ inputs.* }}` expressions into a `run:` shell script, including: `${{ inputs.config }}` (lines 98, 100, 102), `${{ inputs.verbose }}` (line 105), `${{ inputs.dry_run }}` (line 111), `${{ inputs.token }}` (line 117, 119), `${{ inputs.forge }}` (lines 123, 125, 129, 131), `${{ inputs.backend }}` (lines 129, 131), `${{ inputs.registry }}` (lines 135, 137), `${{ inputs.manifest_path }}` (lines 141, 143), `${{ inputs.project_manifest }}` (lines 146, 148), and `${{ inputs.command }}` (lines 153, 175). All of these are interpolated directly into the shell before quoting occurs, allowing a caller-supplied input containing shell metacharacters to inject arbitrary commands. Each should be moved to an `env:` block and referenced as a double-quoted shell variable.

Locations:

- `action.yml:98`
- `action.yml:100`
- `action.yml:102`
- `action.yml:105`
- `action.yml:111`
- `action.yml:117`
- `action.yml:119`
- `action.yml:123`
- `action.yml:125`
- `action.yml:129`
- `action.yml:131`
- `action.yml:135`
- `action.yml:137`
- `action.yml:141`
- `action.yml:143`
- `action.yml:146`
- `action.yml:148`
- `action.yml:153`
- `action.yml:175`

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

Fixed all script-injection findings in action.yml:

1. 'Install release-plz' step: Added `env: INPUT_VERSION: ${{ inputs.version }}` and replaced `release-plz@${{ inputs.version }}` with `"release-plz@${INPUT_VERSION}"` in the run script.

2. 'Run release-plz' step: Added an `env:` block with 10 variables (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND) mapping all ${{ inputs.* }} expressions. Replaced every inline ${{ inputs.* }} reference in the run script with the corresponding $INPUT_* shell variable, all properly double-quoted.

