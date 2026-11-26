# Sharekite plugin

[Sharekite](https://www.sharekite.app/) publishes web pages, reports, and static sites from your agent. You share each page with anyone who has the link, with a password, or only with the people you name, who receive an email invitation. Later, you can publish a new version at the same address.

This repository holds the Sharekite plugin for agent hosts: the `publish-and-share` skill and the connection to the Sharekite MCP server.

## Connect Sharekite

Sharekite is a remote MCP server with OAuth sign-in:

```text
https://studio.sharekite.app/mcp
```

The [setup page](https://www.sharekite.app/connect/) gives the steps for Claude, ChatGPT, Cursor, VS Code, Claude Code, Codex, and other hosts. You can also ask your agent to do the setup:

```text
Read https://www.sharekite.app/connect.md and follow it to connect Sharekite.
```

## Install the plugin in Codex

```sh
codex plugin marketplace add Sharekite/sharekite-plugin
codex plugin add sharekite@sharekite
```

Codex asks you to sign in to Sharekite when the plugin first uses a tool.

## Install the plugin in Claude Code

```sh
claude plugin marketplace add Sharekite/sharekite-plugin
claude plugin install sharekite@sharekite
```

In a session, run `/mcp` and sign in to the `sharekite` server.

## Contents

- [`plugins/sharekite/`](plugins/sharekite/): the plugin package. It connects the agent to the Sharekite MCP server and includes the `publish-and-share` skill in the [Agent Skills](https://agentskills.io/specification) format, which tells the agent when to use Sharekite and which tools to use for each job. Other hosts that read Agent Skills can use the skill folder alone. The package supports both the [Agent Plugins](https://agent-plugins.org/) format, which Codex reads, and the [Claude plugin](https://claude.com/docs/plugins/build) format. Its [README](plugins/sharekite/README.md) describes what the plugin does and which data it sends.
- Marketplace entries at the repository root let Codex and Claude Code install the plugin.

Sharekite generates the content of this repository from its application source for each release, so a pull request here does not change the plugin. Report problems in an issue or at hello@sharekite.app.

## License

The skill and the configuration files are available under the [MIT License](LICENSE). The Sharekite name and logos are not licensed for use.
