# Figgy

Figgy is a home automation and LAN administration project. Join figgy.local today!

- Control all home devices with a single dashboard
- Host movies and personal media
- Handle camera feeds and security monitoring
- Locate household members in real time
- Monitor home power consumption

## Quick Links

All connections must be made within `The Burrow` network.

- [Figgy landing page](https://figgy.local/)
- [Home Assistant](http://figgy.local:8123/)
- [Jellyfin Media Server Home](http://figgy.local:8096/web/)
- [MakeMKV UI](http://figgy.local:5800/)
- [Router](http://192.168.0.1/) (use the wifi password)
- [Portainer](https://figgy.local:9443/#!/3/docker/containers)

## Software

Figgy is a headless Debian server, with most administration handled remotely via SSH and WinSCP tools. Figgy apps are deployed as a docker stack. git is used to control some service configurations, but a deployment pipeline has not yet been developed.

figgy uses a Docker stack of open source microservices. Docker compose file (compose.yml) orchestrates the stack including containers, volumes, and networks. All docker compose commands must be issued in `/opt/figgy`. Start the server with `docker compose up -d`. Stop all services with `docker stop`.

- [Home Assistant](https://www.home-assistant.io/) is a home automation service by the Open Home Foundation. figgy uses [Home Assistant as a unified platform](http://figgy.local:8123) for all home automation integrations.
- [Home Assistant MCP](https://github.com/homeassistant-ai/ha-mcp) is an unofficial Model Context Protocol server for Home Assistant, designed to integrate with AI agents such as Claude. [Connect to MCP](https://figgy.local/mcp) to simplify some development and administration tasks.
- [Caddy](https://caddyserver.com/) is a web server and proxy service. Figgy uses Caddy to manage reverse proxy connections to figgy.local. This keeps communication easy and unbound by dynamic IP addresses.
- [Jellyfin](https://jellyfin.org/) is a media server. Figgy uses Jellyfin for [Media Server portal and streaming](http://figgy.local:8096/web/). Figgy Jellyfin is controlled [via its admin dashboard](http://figgy.local:8096/web/#/dashboard).
- [MakeMKV](https://www.makemkv.com/) is a Bluray transcoder used for media ripping jobs. [jlesage/makemkv](https://hub.docker.com/r/jlesage/makemkv) is an unofficial Docker build of makemkv. Figgy uses MakeMKV to rip Blurays from home library and host video on the media server and [can be controlled remotely](http://figgy.local:5800/).
- [Frigate](https://frigate.video/) is an NVR (Network Video Recorder) service with real-time AI object detection. Figgy uses Frigate for home security camera feeds and monitoring.
- [Portainer Community Edition](https://docs.portainer.io/start/install-ce) is a container administration tool. Figgy uses Portainer is used to easily check [container health and logs](https://figgy.local:9443/#!/3/docker/containers)

## Hardware

**IOT devices** are real devices that figgy interacts with.

- TP-Link lights (Kasa)
- BN-LINK and IR
- TVs and projectors (IR)
- Thermostat (Google Nest)
- 2 automatic cat feeders (Petkit Fresh Element Solo)
- Smart doorbell
- Door locks
- Interior and external home cameras (Tapo)

**Controllers** are interfaces that are used to monitor and control Figgy.

- Home Assistant app for mobile devices
- Switchbot for IR devices like projector and lamps
- TODO Dedicated remote bluetooth control

## Backlog

### Tech debt

Secure data and replace closed source technologies.

- Fix issue with disc not recognized on MakeMKV portal
- Secure all traffic with TLS (remove `NODE_TLS_REJECT_UNAUTHORIZED: 0`)
- Get rid of Tapo cameras - use open hardware with Frigate
- Sysadmin: Add user automation across jellyfin

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
