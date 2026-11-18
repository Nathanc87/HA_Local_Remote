ARG BUILD_FROM
FROM ${BUILD_FROM}

RUN apk add --no-cache \
    bash \
    chromium \
    dbus \
    font-noto \
    font-noto-cjk \
    font-noto-emoji \
    novnc \
    openbox \
    python3 \
    py3-pip \
    ttf-dejavu \
    x11vnc \
    xvfb \
 && python3 -m venv /opt/websockify-venv \
 && /opt/websockify-venv/bin/pip install --no-cache-dir --upgrade pip websockify

COPY rootfs /

RUN chmod a+x /etc/services.d/browser/run

EXPOSE 6080
