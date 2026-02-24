# claude-marketplace

Personal Claude Code plugin marketplace by [Felipe Philipp](https://github.com/felipeelias).

## Installation

```sh
claude plugin install gh:felipeelias/claude-marketplace
```

## Plugins

|Plugin|Description|Version|
|-|-|-|
|[claude-notifier](https://github.com/felipeelias/claude-notifier)|Multi-channel notification dispatcher for Claude Code hooks|0.2.0|

## Adding a plugin

1. Create `plugins/<name>/.claude-plugin/plugin.json` with the plugin manifest
2. Add hooks in `plugins/<name>/hooks/hooks.json` if needed
3. Add an entry to `.claude-plugin/marketplace.json`
4. Run `claude plugin validate .` to verify

## License

[MIT](LICENSE)
