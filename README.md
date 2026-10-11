# Figgy

Figgy is a home automation and LAN administration project. Join figgy.local today!

## Key features

- Control all home devices with a single dashboard
- Host movies and personal media securely
- Handle security monitoring camera feeds, locally and securely
- Monitor household member locations with Home Assistant Companion app
- Monitor home power consumption

## Quick Links

All connections must be made within `The Burrow` network.

- [Home Assistant](http://figgy.local:8123)
- [Router](http://192.168.0.1/) (use the wifi password)
- [Jellyfin Media Server Home](http://figgy.local:8096/web/)
- [Portainer](https://figgy.local:9443/#!/3/docker/containers)
- [Home Assistant MCP](https://figgy.local/mcp)

## Hosting

Figgy is a headless Debian server, with most administration handled remotely via SSH and WinSCP tools. Figgy apps are deployed as a docker stack. git is used to control some service configurations, but a deployment pipeline has not yet been developed.

### Server arch

- /opt/figgy - Home directory for all Docker services and configuration
- /srv/media - All hosted media including movies and personal photos

### Connecting to the server

Connect to `The Burrow` LAN. Administration is handled via SSH (try `ssh user@figgy.local`). Ask Tyler for a user if you don't have one.

## Docker stack

All services are hosted as Docker containers. Docker compose file (compose.yml) orchestrates the stack including containers, volumes, and networks. All docker compose commands must be issued in `/opt/figgy`. Start the server with `docker compose up -d`. Stop all services with `docker stop`.

### Home Assistant

[Home Assistant](https://www.home-assistant.io/) is a free, open source project by the Open Home Foundation. figgy uses [Home Assistant as a unified platform](http://figgy.local:8123) for all home automation integrations.

#### Home Assistant MCP

Connect your AI agent (Claude, Codex, etc) to my figgy's MCP server.

Review existing [Model Context Protocol documentation](https://modelcontextprotocol.io/docs/2026-07-28/develop/connect-local-servers) on local MCP server.

##### Claude setup

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

##### Generated dashboards

Home Assistant MCP is incredibly good at generating dashboards. Try variations of the below prompt.

`Generate a new Home Assistant dashboard called "Command Center". This is a Star Trek themed dashboard with jellyfin media and KMHD radio player at the top and light controls at the bottom.`

### Caddy

[Caddy](https://caddyserver.com/) is a free, open source web server and proxy service, Figgy uses Caddy to manage reverse proxy connections to figgy.local. This keeps communication easy and unbound by dynamic IP addresses.

### Jellyfin

[Jellyfin](https://jellyfin.org/) is an free, open source media server. Figgy uses Jellyfin for [Media Server portal and streaming](http://figgy.local:8096/web/). Figgy Jellyfin is controlled [via its admin dashboard](http://figgy.local:8096/web/#/dashboard).

### Frigate

[Frigate](https://frigate.video/) is a free NVR (Network Video Recorder) with real-time AI object detection on local systems. Figgy uses Frigate for home security camera feeds and monitoring.

### Portainer

[Portainer Community Edition](https://hub.docker.com/r/portainer/portainer-ce) is a free, open source container administration tool. Figgy uses Portainer is used to easily check [container health and logs](https://figgy.local:9443/#!/3/docker/containers)

## Hardware

Below is a list of real devices that figgy integrates

### IOT devices
- Lights (Kasa and BN-LINK and IR)
- TVs and projectors (IR)
- Thermostat (Google Nest)
- 2 automatic cat feeders (Petkit Fresh Element Solo)
- Smart doorbell
- Door locks
- Interior and external home cameras (Tapo)

### Controllers

Controllers are interfaces that are used to monitor and control Figgy.

- Tablet device with Android app, restricted to LAN.
- iPhone device iOS app with full control of home automation
- Android app with camera feed
- Dedicated remote control for IR devices like TVs
- Dedicated remote bluetooth control

## Backlog

Stuff I want to do later.

- Sysadmin: Add user automation across jellyfin

### Tech debt

Secure data and replace closed source technologies.

- Secure all traffic with TLS (remove `NODE_TLS_REJECT_UNAUTHORIZED: 0`)
- Get rid of Tapo cameras - use open hardware with Frigate

### Feature wishlist

- Home intercom and audio system integration
- Outdoor weather station
- Garage door control
- Smoke detector
- Gas leak detector
- Flooding / water detector
- LG dishwasher with ThinQ integration
- LG refrigerator with ThinQ integration
- Coffee maker with manual toggles
- HDMI switch with audio output to soundbar via HDMI eARCs
- Push notifications for alerting systems like smoke detectors
- Push notifications for motion detected on cameras
