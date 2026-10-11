# Figgy

Figgy is a home automation and LAN administration project by Tyler Fluegel. Join figgy.local today!

## Connecting to the server

Connect to `The Burrow` LAN. Figgy server is headless, with most administration via SSH (try `ssh user@figgy.local`). Ask Tyler for a user if you don't have one.

## Quick Links

- [Router](
http://192.168.0.1/)
Wifi password
- [Home Assistant](http://figgy.local:8123)
- [Jellyfin Media Server Home](http://figgy.local:8096/web/)
- [Portainer](https://figgy.local:9443/#!/3/docker/containers)
- [Home Assistant MCP](https://figgy.local/mcp)

## Hosting

All services are hosted as docker containers. The compose.yml contains the definition of all containerized services, volumes, and networks. Start the server with `docker compose up -d`. Stop all services with `docker stop`

## Home Assistant

[figgy Home Assistant](http://figgy.local:8123) is the platform for all home automation features

[Home Assistant](https://www.home-assistant.io/) is a free, open source project by the Open Home Foundation.

### Home Assistant MCP

Connect your AI agent (Claude, Codex, etc) to my local MCP server

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

## Caddy

[Caddy](https://caddyserver.com/) is a free, open source web server and proxy service, use for managing reverse proxy connections to figgy.local. This keeps communication easy and unbound by dynamic IP addresses.



## Jellyfin

[figgy Jellyfin admin dashboard](http://figgy.local:8096/web/#/dashboard)

[Jellyfin](https://jellyfin.org/) is an free, open source media server.

## Portainer

[figgy Portainer](https://figgy.local:9443/#!/3/docker/containers)

[Portainer Community Edition](https://hub.docker.com/r/portainer/portainer-ce) is a free, open source container administration tool.



## Backlog
- Sysadmin: Add user automation across jellyfin