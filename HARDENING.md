<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.134

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.134** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' run: block directly interpolates `${{ inputs.version }}` into a shell command string (`cargo-binstall release-plz@${{ inputs.version }}`). A caller-controlled value is substituted by the YAML template engine before the shell ever sees it, enabling command injection if the input contains shell metacharacters.

Locations:

- `action.yml:84`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' run: block directly interpolates multiple `${{ inputs.* }}` expressions into shell command strings without routing them through env: variables. Affected inputs: `inputs.config` (used in `if [[ -n "${{ inputs.config }}" ]]`, `echo`, and array assignment), `inputs.verbose`, `inputs.dry_run`, `inputs.token` (passed as `--token` argument), `inputs.forge`, `inputs.backend`, `inputs.registry`, `inputs.manifest_path`, `inputs.project_manifest`, and `inputs.command` (used in `[[ -z "${{ inputs.command }}" || "${{ inputs.command }}" == "release-pr" ]]` and the release branch). All of these are YAML-template-substituted before the shell parses the script, allowing an attacker-controlled value to inject arbitrary shell commands.

Locations:

- `action.yml:91`
- `action.yml:93`
- `action.yml:95`
- `action.yml:99`
- `action.yml:104`
- `action.yml:109`
- `action.yml:111`
- `action.yml:114`
- `action.yml:116`
- `action.yml:118`
- `action.yml:121`
- `action.yml:127`
- `action.yml:129`
- `action.yml:133`
- `action.yml:135`
- `action.yml:137`
- `action.yml:139`
- `action.yml:143`
- `action.yml:163`

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

1. 'Install release-plz' step: Added env: block with INPUT_VERSION=${{ inputs.version }} and replaced the inline ${{ inputs.version }} in the run: block with $INPUT_VERSION.

2. 'Run release-plz' step: Added env: block with 10 variables (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND) mapping all ${{ inputs.* }} expressions. Replaced all inline ${{ inputs.* }} references throughout the run: block with the corresponding $INPUT_* environment variable references.

All ${{ inputs.* }} expressions now appear only in env: blocks (safe), not in run: shell strings.

