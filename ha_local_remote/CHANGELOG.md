# Changelog

## 0.1.3
- Restore build.yaml to provide architecture-specific BUILD_FROM to Docker builds.
- Keep build.yaml despite Supervisor deprecation warning because the current build requires the base image mapping.

## 0.1.2
- Replace unavailable Alpine py3-websockify package with websockify installed in an isolated Python virtual environment.
- Remove deprecated build.yaml; Home Assistant supplies BUILD_FROM directly to the Dockerfile.

## 0.1.1
- First Chromium/noVNC browser prototype.
- Persistent browser profile.

## 0.1.0
- Initial Home Assistant add-on scaffold.
