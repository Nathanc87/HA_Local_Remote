# HA Local Remote

Home Assistant add-on for browsing local HTTP and HTTPS device interfaces through Home Assistant Ingress.

## Status
Early development. This repository is the starting point for the browser prototype.

## Planned architecture
Chromium runs inside an add-on container on the Home Assistant network. The browser display is streamed to the Home Assistant frontend through an authenticated Ingress session using noVNC.

## Security
- Do not expose the add-on's browser or VNC ports directly to the internet.
- Keep access behind Home Assistant authentication.
- The first prototype is a shared browser session and is not production-hardened.
- Destination restrictions, session isolation, and secure handling of downloads are required before treating this as a general-purpose remote access tool.
