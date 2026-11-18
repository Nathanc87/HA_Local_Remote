# HA Local Remote

A Home Assistant add-on that runs a real Chromium browser on your Home Assistant network and streams its desktop into the Home Assistant interface.

## Version 0.1.1 — first browser build

This first build provides a remote Chromium desktop through noVNC. You get the normal Chromium window, including its address bar, tabs, navigation buttons, cookies and website JavaScript. Enter internal URLs such as:

- `http://192.168.1.1`
- `https://192.168.1.10`
- `http://my-server.local:8080`

The browser makes the network requests from inside the add-on container, not from your phone or desktop. This is what allows it to reach LAN-only devices while you are away.

## Install

1. In Home Assistant, open **Settings → Add-ons → Add-on Store**.
2. Open the three-dot menu and choose **Repositories**.
3. Add `https://github.com/Nathanc87/HA_Local_Remote`.
4. Find **HA Local Remote** under the local add-ons, install it and start it.
5. Open the add-on's **Network Browser** panel.

If the repository does not appear immediately, refresh the add-on store.

## How it works

- Chromium runs inside the add-on on the Home Assistant network.
- Xvfb provides a virtual 1440×900 display.
- Openbox manages the Chromium window.
- x11vnc exposes the display only on loopback inside the container.
- noVNC/websockify streams the display through Home Assistant Ingress.

The Chromium profile is stored in `/share/ha_local_remote/chromium`, so cookies and sessions persist across restarts.

## Important limitations

This is the first functional browser build, not a finished polished browser application.

- The interface is a streamed desktop, not yet a custom address-bar/bookmark UI.
- It uses one shared Chromium profile/session.
- Mobile use is supported by the responsive noVNC client, but small-screen interaction may be less comfortable than desktop.
- Bookmarks, browser history controls outside Chromium, per-user sessions, downloads management and configurable display size are not implemented yet.
- The container has broad access to the networks reachable from Home Assistant. There is not yet a destination allow-list.

## Security

- Keep access behind Home Assistant authentication and Ingress.
- Do not expose port 6080 or VNC port 5900 directly to the internet.
- Use a strong Home Assistant account and MFA.
- Anyone permitted to open this add-on can control its shared browser session and access devices reachable from the add-on.
- Treat this initial version as experimental and install only on a trusted network.

## Supported architectures

amd64 and aarch64.

## Troubleshooting

- If the panel is blank, check the add-on log for Chromium, Xvfb or websockify startup errors.
- If the browser opens but a device does not load, check that the add-on can route to that device's subnet and that the device permits HTTP/HTTPS access.
- Internal DNS names require the add-on container to use a DNS server that can resolve them.
- Self-signed HTTPS certificates may show browser warnings. Only proceed when you trust the device and its certificate.
