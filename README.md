# claude-marketplace

Personal Claude Code plugin marketplace by [Felipe Philipp](https://github.com/felipeelias).

## Installation

### From Claude Code (recommended)

1. Run `/plugin` and select **Add marketplace**
2. Enter `felipeelias/claude-marketplace`
3. Run `/plugin` again and install available plugins

### From the CLI

```sh
# Add marketplace (one-time)
claude plugin marketplace add felipeelias/claude-marketplace

# Install plugin
claude plugin install claude-notifier@felipe-philipp
```

## Plugins

|Plugin|Description|Version|
|-|-|-|
|[claude-notifier](https://github.com/felipeelias/claude-notifier)|Multi-channel notification dispatcher for Claude Code hooks|0.2.0|
|github-tools|GitHub CLI tools for CI monitoring, PR management, and workflow automation|0.2.0|

## Adding a plugin

1. Create `plugins/<name>/.claude-plugin/plugin.json` with the plugin manifest
2. Add hooks in `plugins/<name>/hooks/hooks.json` if needed
3. Add skills in `plugins/<name>/skills/<skill>/SKILL.md` if needed
4. Add an entry to `.claude-plugin/marketplace.json`
5. Run `claude plugin validate .` to verify

## License

[MIT](LICENSE)
