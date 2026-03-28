# Claude Marketplace

Personal Claude Code plugin marketplace.

## Structure

- `.claude-plugin/marketplace.json` — marketplace registry
- `plugins/<name>/.claude-plugin/plugin.json` — plugin manifest
- `plugins/<name>/hooks/hooks.json` — plugin hooks
- `plugins/<name>/skills/<skill>/SKILL.md` — plugin skills
- `skills/` — marketplace management skills

## Conventions

- Plugin names use kebab-case
- Versions follow semver
- Plugin sources use relative paths (`./plugins/<name>`)
- Keep marketplace.json plugin entries in sync with plugin.json manifests
- plugin.json is the source of truth for plugin metadata

## Linting

- Markdown: `markdownlint-cli2` (config: `.markdownlint-cli2.jsonc`)
- JSON: `biome check .` (config: `biome.json`)
- YAML: `yamllint .` (config: `.yamllint.yml`)

## Validation

```sh
claude plugin validate .
```

Or use the `/validate-marketplace` skill to check manifest sync and hooks.
