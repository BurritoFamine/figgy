# Figgy

Figgy is a home automation and services server built with Home Assistant.

## Requirements

Figgy is a complete and secure home automation system.

- Centralize control of all device in my home on a single app
- Schedule control of devices such as theromstat and lighting

### Future considerations

These features are low priority but may be implemented in the future. Ensure Figgy is prepared to handle these.

- Push notifications for alerting systems like smoke detectors
- Push notifications for motion detected on cameras
- Weather service integration

## Devices
Figgy should integrate with all devices in the home. If device uses HTTP, suggest open source and secure options. If device does not use HTTP, suggest hardware to allow device to communicate with Figgy.

### My devices
- Lights (Kasa and BN-LINK and IR)
- TVs and projectors (IR)
- Thermostat (Google Nest)
- 2 automatic cat feeders (Petkit Fresh Element Solo)
- Smart doorbell
- Door locks
- Interior and external home cameras (Tapo)

### Future considerations

These devices are low priority but may be implemented in the future. Ensure Figgy is prepared to handle these.

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

## Controllers

Controllers are interfaces that are used to monitor and control Figgy. I should be capable of monitoring and controlling Figgy with the following controllers.

- Tablet device with Android app, restricted to LAN.
- iPhone device iOS app with full control of home automation
- Android app with camera feed
- Dedicated remote control for IR devices like TVs

## Architecture

### Security and Privacy

Figgy should use all open source technogies controlled by me. Figgy should always use HTTPS, secure websockets, encryption, and all other security best practices. Figgy control points should always use 2FA. All Figgy traffic should be restricted to LAN. Figgy can only be controlled outside of LAN using iOS and Andriod apps. Figgy control should only allow connections through trusted proxies on my VPN, and only when required (for example, viewing security cameras when away from home). Enforce all best practices documented by Home Assistant.
Apply the STRIDE model and outline security requirements.


### Software

Home Automation will be the foundation of Figgy. I am comfortable building and deploying containerized software onto my raspberry pi devices. I need an online portal and dashboard accessed via LAN at localhost. Suggest a "control panel" UI for tablet devices created by Home Automation, but I will probably be interested in building my own. I need an Android and iOS app that are also capable of controlling Figgy and viewing cameras.

### Hardware

Hardware should be secure. Ideally it should be open source and popular with the Home Assistant community. I can develop my own hardware with a raspberry pi and a breadboard where appropriate.
Server

Home Automation server must be hosted locally on dedicated hardware. I should be able to fork my own build of Home Automation and deploy it to the hardware. Describe the benefits of containerization.

#### Devices

Device traffic should always be encrypted and secure.

#### Networking

##### Protocols
IR, HTTPS, and RFID are acceptable. List any other protocols that are going to be used in this.

Create a network diagram of Figgy with devices and required network infrastructure for security.