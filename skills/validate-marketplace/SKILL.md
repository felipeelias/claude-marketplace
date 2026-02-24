---
name: validate-marketplace
description: This skill should be used when the user asks to "validate the marketplace", "check marketplace sync", "verify plugin manifests", "validate marketplace.json", or mentions marketplace validation or plugin sync issues.
---

# Validate Marketplace

Validate that marketplace.json plugin entries are in sync with their corresponding plugin.json manifests and that all files follow required conventions.

## Validation Checks

Run each check in order. Report all issues found, then summarize pass/fail.

### 1. Marketplace Structure

Verify `.claude-plugin/marketplace.json` exists and contains valid JSON with these required fields:

- `$schema` — must reference the Anthropic marketplace schema
- `name` — marketplace name in kebab-case
- `owner` — object with `name` (and optionally `email`)
- `plugins` — non-empty array

### 2. Plugin Entry Completeness

For each entry in `plugins[]`, verify these fields are present:

| Field | Required | Notes |
|-------|----------|-------|
| `name` | Yes | kebab-case |
| `source` | Yes | relative path starting with `./plugins/` |
| `description` | Yes | non-empty string |
| `version` | Recommended | semver format |
| `author` | Recommended | object with `name` |
| `category` | Recommended | one of: development, productivity, security, database, testing |
| `license` | Recommended | e.g. MIT, Apache-2.0 |

### 3. Plugin Source Exists

For each plugin entry with a relative `source` path, verify:

- The directory at `source` exists
- It contains `.claude-plugin/plugin.json`

### 4. Manifest Sync

For each plugin, compare the marketplace.json entry against the plugin's own `plugin.json`. Flag mismatches in:

- `name`
- `description`
- `version`
- `author.name`
- `license`

The plugin.json is the source of truth. If values differ, recommend updating marketplace.json.

### 5. Hooks Validation

If a plugin directory contains `.claude-plugin/hooks.json`, verify:

- Valid JSON
- Has a `hooks` object containing at least one event key
- Event keys are valid: `PreToolUse`, `PostToolUse`, `Stop`, `SubagentStop`, `SessionStart`, `SessionEnd`, `UserPromptSubmit`, `PreCompact`, `Notification`

## Output Format

Present results as a checklist:

```
## Marketplace Validation Results

- [x] Marketplace structure valid
- [x] Plugin entries complete (N plugins)
- [ ] Manifest sync — version mismatch for "plugin-name" (marketplace: 0.1.0, plugin: 0.2.0)
- [x] Hooks configuration valid
```

End with a summary: total checks passed, total warnings, total errors.
