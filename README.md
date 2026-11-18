# HA Local Remote

A Home Assistant add-on that runs a real Chromium browser on your Home Assistant network and streams its desktop into Home Assistant.

## Version 0.1.2

First browser prototype, with a build dependency fix for websockify.

- Chromium runs inside the add-on on the Home Assistant network.
- noVNC streams the browser desktop through Home Assistant Ingress.
- Normal Chromium address bar, tabs, cookies and website JavaScript.
- Persistent browser profile under `/share/ha_local_remote/chromium`.

## Install

1. In Home Assistant, open **Settings → Add-ons → Add-on Store**.
2. Open the three-dot menu and choose **Repositories**.
3. Add `https://github.com/Nathanc87/HA_Local_Remote`.
4. Refresh the store, install **HA Local Remote**, then start it.
5. Open the **Network Browser** panel.

## Try

- `http://192.168.1.1`
- `https://192.168.1.10`
- `http://device-hostname.local:8080`

Requests originate from the add-on container, not from your phone or desktop.

## Architecture

Chromium runs under Xvfb and Openbox. x11vnc listens on loopback only; websockify/noVNC exposes the display through the add-on's Ingress port.

## Limitations and security

This is experimental and has not yet been validated on every Home Assistant architecture.

- One shared Chromium session; anyone allowed to open the panel can control it.
- No destination allow-list, per-user isolation, custom bookmarks, or download manager yet.
- Keep it behind Home Assistant authentication. Do not expose ports 6080 or 5900 directly to the internet.
- The add-on can reach networks routable from the Home Assistant host. Use only on a trusted network.
- Self-signed HTTPS certificates may display browser warnings.
