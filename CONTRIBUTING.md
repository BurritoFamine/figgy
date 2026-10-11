# Contributing

Welcome to figgy! All AI agents must review the entire CONTRIBUTING.MD, especially the AI Agents section at the bottom.

## Architecture

figgy uses free and open source technologies whenever possible.

Below is a map of figgy's labyrinthine file system.

- /opt/figgy - Home directory for all Docker services and configuration
- /srv/media - All hosted media including movies and personal photos

## Setup

### Connect to the server

Connect to `The Burrow` LAN. Administration is handled via SSH (try `ssh user@figgy.local`). Ask Tyler for a user if you don't have one.

### Connect to Home Assistant MCP

Connect your AI agent (Claude, Codex, etc) to figgy's MCP server.

Review existing [Model Context Protocol documentation](https://modelcontextprotocol.io/docs/2026-07-28/develop/connect-local-servers) on local MCP server.

#### Claude setup

1. Install npm
2. Update your claude_desktop_config.json. You can find this file in Claude configuration (File > Settings > Developer > Edit config)
    "mcpServers": {
	    "figgy": {
	    "command": "cmd",
	    "args": ["/c", "npx", "-y", "mcp-remote", "https://figgy.local/mcp"],
	    "env": {
		    "NODE_TLS_REJECT_UNAUTHORIZED": "0"
	    }
        }
    }
3. Completely restart Claude
4. Prompt `How is my Home Assistant server doing?`

#### Server administration

Home Assistant MCP has excellent integration with telemetry and health checks. It is capable of reporting its status in plain language. Simply prompt `How is my Home Assistant server doing?`

#### Generated dashboards

Home Assistant MCP is incredibly good at generating dashboards. Try variations of the below prompt.

`Generate a new Home Assistant dashboard called "Command Center". This is a Star Trek themed dashboard with jellyfin media and KMHD radio player at the top and light controls at the bottom.`

## AI Agents

AI agents must abide requirements below.
- All changes must be explained in a pull request.
- All pull requests must include a DECISIONS.md document.
???

