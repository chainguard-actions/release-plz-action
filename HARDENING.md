<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.140

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.140** was hardened automatically. 29 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' step directly interpolates `${{ inputs.version }}` inside a `run:` shell command string: `release-plz@${{ inputs.version }}`. Before the shell ever sees this string, GitHub Actions performs YAML template substitution, allowing an attacker-controlled value to inject arbitrary shell metacharacters (e.g. a version like `0.3.170 --no-confirm; curl ... | bash`). The fix is to pass the value via an `env:` variable and reference it as a quoted shell variable: `env: VERSION: ${{ inputs.version }}` then `release-plz@"$VERSION"`.

Locations:

- `action.yml:86`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' step directly interpolates multiple `${{ inputs.* }}` expressions inside a `run:` shell command string. Affected inputs include: `inputs.config` (used in `if [[ -n "${{ inputs.config }}" ]]` and `CONFIG_PATH=("--config" "${{ inputs.config }}")`), `inputs.verbose`, `inputs.dry_run`, `inputs.token` (used in `TOKEN=("--token" "${{ inputs.token }}")`), `inputs.forge`, `inputs.backend`, `inputs.registry`, `inputs.manifest_path`, `inputs.project_manifest`, and `inputs.command`. All of these are interpolated directly into the shell script before the shell parses it, enabling script injection via crafted input values containing shell metacharacters (e.g. `"; malicious-command #`). The fix is to map each input to an `env:` variable and reference it as a double-quoted shell variable throughout the script.

Locations:

- `action.yml:97`
- `action.yml:99`
- `action.yml:101`
- `action.yml:107`
- `action.yml:109`
- `action.yml:113`
- `action.yml:115`
- `action.yml:117`
- `action.yml:119`
- `action.yml:123`
- `action.yml:125`
- `action.yml:129`
- `action.yml:131`
- `action.yml:133`
- `action.yml:137`
- `action.yml:139`
- `action.yml:143`
- `action.yml:145`
- `action.yml:148`
- `action.yml:175`

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

1. 'Install release-plz' step: Moved `${{ inputs.version }}` to an `env:` block as `INPUT_VERSION`, then referenced it as `"release-plz@${INPUT_VERSION}"` in the run: script.

2. 'Run release-plz' step: Moved all 10 `${{ inputs.* }}` expressions to an `env:` block (INPUT_CONFIG, INPUT_VERBOSE, INPUT_DRY_RUN, INPUT_TOKEN, INPUT_FORGE, INPUT_BACKEND, INPUT_REGISTRY, INPUT_MANIFEST_PATH, INPUT_PROJECT_MANIFEST, INPUT_COMMAND), then replaced every inline `${{ inputs.X }}` reference throughout the shell script with the corresponding `$INPUT_X` shell variable.

All remaining `${{ inputs.* }}` occurrences in the file are in safe locations: env: value assignments, an if: condition (GitHub Actions expression context, not shell), and outputs: value references.

