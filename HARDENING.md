<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.138

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.138** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' run: block directly interpolates ${{ inputs.version }} into a shell command string. An attacker-controlled value for this input could inject arbitrary shell commands before the shell ever sees the string. The offending line is: `release-plz@${{ inputs.version }}\`. The fix is to pass the version via an env: variable and reference it as a quoted shell variable (e.g., `"$RELEASE_PLZ_VERSION"`).

Locations:

- `action.yml:88`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' run: block directly interpolates multiple ${{ inputs.* }} expressions into shell command strings. Every one of these is substituted by the GitHub Actions template engine before the shell parses the script, allowing an attacker-controlled input to inject arbitrary shell commands. Affected inputs and representative lines include:
- ${{ inputs.config }} (lines 95, 97, 99) — used in `if [[ -n "${{ inputs.config }}" ]]` and `CONFIG_PATH=("--config" "${{ inputs.config }}")`
- ${{ inputs.verbose }} (line 104) — used in `if [[ -n "${{ inputs.verbose }}" ]]`
- ${{ inputs.dry_run }} (line 109) — used in `if [[ -n "${{ inputs.dry_run }}" ]]`
- ${{ inputs.token }} (lines 114, 116) — used in `if [[ -n "${{ inputs.token }}" ]]` and `TOKEN=("--token" "${{ inputs.token }}")`
- ${{ inputs.forge }} (lines 119, 121, 122) — used in conditionals and `FORGE=("--forge" "${{ inputs.forge }}")`
- ${{ inputs.backend }} (lines 123, 126, 127) — used in conditionals and `FORGE=("--forge" "${{ inputs.backend }}")`
- ${{ inputs.registry }} (lines 133, 135, 136) — used in conditionals and `ALT_REGISTRY=("--registry" "${{ inputs.registry }}")`
- ${{ inputs.manifest_path }} (lines 140, 142, 143) — used in conditionals and `MANIFEST_PATH=("--manifest-path" "${{ inputs.manifest_path }}")`
- ${{ inputs.project_manifest }} (lines 144, 146, 147) — used in conditionals and `MANIFEST_PATH=("--project-manifest" "${{ inputs.project_manifest }}")`
- ${{ inputs.command }} (lines 151, 168) — used in `if [[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release-pr" ]]`
All of these should be moved to env: variables and referenced as quoted shell variables.

Locations:

- `action.yml:95`
- `action.yml:97`
- `action.yml:99`
- `action.yml:104`
- `action.yml:109`
- `action.yml:114`
- `action.yml:116`
- `action.yml:119`
- `action.yml:121`
- `action.yml:122`
- `action.yml:123`
- `action.yml:126`
- `action.yml:127`
- `action.yml:133`
- `action.yml:135`
- `action.yml:136`
- `action.yml:140`
- `action.yml:142`
- `action.yml:143`
- `action.yml:144`
- `action.yml:146`
- `action.yml:147`
- `action.yml:151`
- `action.yml:168`

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
1. 'Install release-plz' step: moved ${{ inputs.version }} to env: block as RELEASE_PLZ_VERSION, referenced as "${RELEASE_PLZ_VERSION}" in the run: shell script.
2. 'Run release-plz' step: moved all 10 inputs (config, verbose, dry_run, token, forge, backend, registry, manifest_path, project_manifest, command) to an env: block with INPUT_* names. All occurrences in the run: block now reference the corresponding shell variables ($INPUT_CONFIG, $INPUT_VERBOSE, $INPUT_DRY_RUN, $INPUT_TOKEN, $INPUT_FORGE, $INPUT_BACKEND, $INPUT_REGISTRY, $INPUT_MANIFEST_PATH, $INPUT_PROJECT_MANIFEST, $INPUT_COMMAND). No ${{ }} expressions remain in any run: block.

