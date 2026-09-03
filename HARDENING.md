<!-- markdownlint-disable -->

# Hardening Report: release-plz--action/v0.5.132

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **release-plz--action/v0.5.132** was hardened automatically. 30 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### script-injection (severity: high)

Sub-rule (a): The 'Install release-plz' step directly interpolates ${{ inputs.version }} into a run: shell command: `release-plz@${{ inputs.version }}\`. A caller-controlled value is expanded by the YAML template engine before the shell ever sees it, allowing an attacker to inject arbitrary shell commands via the version input.

Locations:

- `action.yml:89`

### script-injection (severity: high)

Sub-rule (a): The 'Run release-plz' step directly interpolates multiple ${{ inputs.* }} expressions into a run: shell script, including: ${{ inputs.config }}, ${{ inputs.verbose }}, ${{ inputs.dry_run }}, ${{ inputs.token }}, ${{ inputs.forge }}, ${{ inputs.backend }}, ${{ inputs.registry }}, ${{ inputs.manifest_path }}, ${{ inputs.project_manifest }}, and ${{ inputs.command }}. Each of these is expanded by the YAML template engine before the shell processes the script, allowing an attacker to inject arbitrary shell commands through any of these inputs.

Locations:

- `action.yml:99`

### script-injection (severity: high)

Sub-rule (a): The 'Update major tag' step in update_main_version.yml directly interpolates ${{ secrets.GITHUB_TOKEN }} into a run: shell command: `git remote set-url origin "https://x-access-token:${{ secrets.GITHUB_TOKEN }}@github.com/${GITHUB_REPOSITORY}.git"`. Any ${{ ... }} expression directly inside a run: block is a script-injection risk as the value is substituted by the template engine before the shell processes the command.

Locations:

- `.github/workflows/update_main_version.yml:21`

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

Fixed all script injection findings across two files:

1. hardened/action/action.yml - 'Install release-plz' step: Moved ${{ inputs.version }} to env: block as INPUT_VERSION.

2. hardened/action/action.yml - 'Run release-plz' step: Moved all 10 inputs (${{ inputs.config }}, ${{ inputs.verbose }}, ${{ inputs.dry_run }}, ${{ inputs.token }}, ${{ inputs.forge }}, ${{ inputs.backend }}, ${{ inputs.registry }}, ${{ inputs.manifest_path }}, ${{ inputs.project_manifest }}, ${{ inputs.command }}) to an env: block with INPUT_* names, and replaced all inline template expressions with plain environment variable references throughout the shell script.

3. hardened/action/.github/workflows/update_main_version.yml - 'Update major tag' step: Moved ${{ secrets.GITHUB_TOKEN }} to env: block as GH_TOKEN, and replaced the inline expression with ${GH_TOKEN} in the git remote set-url command.

All ${{ ... }} expressions have been removed from run: blocks and are now safely passed through the env: mechanism.

