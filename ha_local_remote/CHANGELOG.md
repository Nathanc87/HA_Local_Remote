# Changelog

## 0.1.5
- Configure noVNC to connect automatically and scale the remote desktop to the available viewport.
- Explicitly disable Vulkan and request SwiftShader software rendering for Chromium in the virtual display.

## 0.1.4
- Set Home Assistant Ingress entry point to noVNC's vnc.html.

## 0.1.3
- Restore build.yaml to provide architecture-specific BUILD_FROM to Docker builds.

## 0.1.2
- Replace unavailable Alpine py3-websockify package with websockify installed in an isolated Python virtual environment.

## 0.1.1
- First Chromium/noVNC browser prototype.
- Persistent browser profile.

## 0.1.0
- Initial Home Assistant add-on scaffold.
