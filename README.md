# agentic-tools

A Claude Code plugin marketplace with agentic tooling. Add it once, then install any plugin from it.

## Add the marketplace

```
/plugin marketplace add f0ster/agentic-tools
```

## Plugins

### `cove` — Chain-of-Verification validation

Rigorously verifies the correctness of a claim, output, plan, or code change using the [Chain-of-Verification](https://arxiv.org/abs/2309.11495) (CoVe) framework: it generates independent verification questions, answers each by actually checking (reading files, running commands, querying state) without bias from the original draft, then synthesizes a verified result.

Install:

```
/plugin install cove@agentic-tools
```

Use it:

- **Explicit command:** `/cove <what to verify>` — append `quick` for a shallow 3-question pass or `thorough` for a deep 5-7 question pass.
- **Automatically:** the skill triggers on its own when you say things like "validate this", "verify that", "is this right?", or before committing code and finalizing plans.

## Adding more plugins

Each plugin lives in its own directory under `plugins/` with a `.claude-plugin/plugin.json`, and is registered as an entry in `.claude-plugin/marketplace.json`:

```
agentic-tools/
├── .claude-plugin/
│   └── marketplace.json        # registry of all plugins
└── plugins/
    └── cove/
        ├── .claude-plugin/
        │   └── plugin.json
        ├── skills/
        │   └── cove/SKILL.md
        └── commands/
            └── cove.md
```

To add a plugin: create `plugins/<name>/` with its `plugin.json` (plus any `skills/`, `commands/`, `agents/`, `hooks/`), then append an entry to the `plugins` array in `marketplace.json`.

## License

MIT
