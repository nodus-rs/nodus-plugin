# nodus-plugin

`nodus-plugin` is the shareable package content behind Nodus helper workflows.

It ships reusable:

- skills for consuming, authoring, and troubleshooting Nodus packages
- agents for package guidance and package review
- commands for common install, inspect, and sync flows
- a usage rule for consistent Nodus behavior

The repo is designed to be consumed as a Nodus package and also includes native plugin metadata for Claude Code and Codex.
For day-to-day usage, `nodus --help` is the quickest way to discover the supported commands and examples.

## What Is Included

Current package contents:

- Skills: `nodus-consumer`, `nodus-package-author`, `nodus-troubleshooting`
- Agents: `nodus-guide`, `nodus-package-reviewer`
- Commands: `add-package`, `inspect-package`, `sync-and-verify`
- Rules: `nodus-usage`

## Install With Nodus

Use Nodus when you want this package managed in the current workspace.

Examples:

```bash
nodus add nodus-rs/nodus-plugin --adapter codex
nodus add nodus-rs/nodus-plugin --adapter claude
nodus add nodus-rs/nodus-plugin --adapter claude --component skills --component rules
nodus doctor
```

Guidelines:

- Prefer project-scoped installs by default: `nodus add nodus-rs/nodus-plugin --adapter <adapter>`.
- Use `--global` only when the user explicitly wants a home-scoped install.
- Prefer the full package unless you only need a subset of `skills`, `agents`, `commands`, or `rules`.
- Prefer tagged releases when installing from Git.
- Let Nodus manage generated runtime files under `.codex/`, `.claude/`, `.agents/`, and similar adapter roots.

## Plugin Metadata

This repository also exposes plugin metadata for native plugin workflows:

- Claude Code plugin manifest: [.claude-plugin/plugin.json](./.claude-plugin/plugin.json)
- Claude marketplace catalog: [.claude-plugin/marketplace.json](./.claude-plugin/marketplace.json)
- Codex plugin manifest: [.codex-plugin/plugin.json](./.codex-plugin/plugin.json)
- Nodus compatibility metadata: [claude-code.json](./claude-code.json)

Those files describe the same package content already stored in this repo root. They do not replace Nodus package discovery.

## Repository Layout

```text
skills/
agents/
commands/
rules/
.claude-plugin/
.codex-plugin/
claude-code.json
```

Artifact layout follows the normal Nodus package conventions:

- `skills/<id>/SKILL.md`
- `agents/<id>.md`
- `commands/<id>.md`
- `rules/<id>.md`

## Development

Useful checks while editing the package:

```bash
nodus info .
claude plugin validate .
claude plugin validate .claude-plugin/plugin.json
```

If you are testing from a consuming workspace, finish with:

```bash
nodus doctor
```

## License

[MIT](./LICENSE)
