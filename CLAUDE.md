# Claude Marketplace

Personal Claude Code plugin marketplace.

## Structure

- `.claude-plugin/marketplace.json` — marketplace registry
- `plugins/<name>/.claude-plugin/plugin.json` — plugin manifest
- `plugins/<name>/.claude-plugin/hooks.json` — plugin hooks

## Conventions

- Plugin names use kebab-case
- Versions follow semver
- Plugin sources use relative paths (`./plugins/<name>`)
- Keep marketplace.json plugin entries in sync with plugin.json manifests

## Validation

```sh
claude plugin validate .
```
