# Figgy

Figgy is a home automation and LAN administration project. Join figgy.local today!

## Key features

figgy handles many home automations and tasks securely and locally, using open source hardware and software whenever possible.

- Control all home devices with a single dashboard
- Host movies and personal media
- Handle camera feeds and security monitoring
- Locate household members in real time
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

All services are open source are hosted as Docker containers. Docker compose file (compose.yml) orchestrates the stack including containers, volumes, and networks. All docker compose commands must be issued in `/opt/figgy`. Start the server with `docker compose up -d`. Stop all services with `docker stop`.

- [Home Assistant](https://www.home-assistant.io/) is a home automation service by the Open Home Foundation. figgy uses [Home Assistant as a unified platform](http://figgy.local:8123) for all home automation integrations.
- [Home Assistant MCP](https://github.com/homeassistant-ai/ha-mcp) is an unofficial Model Context Protocol server for Home Assistant, designed to integrate with AI agents such as Claude. figgy uses MCP to simplify some development and administration tasks.
- [Caddy](https://caddyserver.com/) is a web server and proxy service. Figgy uses Caddy to manage reverse proxy connections to figgy.local. This keeps communication easy and unbound by dynamic IP addresses.
- [Jellyfin](https://jellyfin.org/) is a media server. Figgy uses Jellyfin for [Media Server portal and streaming](http://figgy.local:8096/web/). Figgy Jellyfin is controlled [via its admin dashboard](http://figgy.local:8096/web/#/dashboard).
- [Frigate](https://frigate.video/) is an NVR (Network Video Recorder) service with real-time AI object detection. Figgy uses Frigate for home security camera feeds and monitoring.
- [Portainer Community Edition](https://docs.portainer.io/start/install-ce) is a container administration tool. Figgy uses Portainer is used to easily check [container health and logs](https://figgy.local:9443/#!/3/docker/containers)

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
