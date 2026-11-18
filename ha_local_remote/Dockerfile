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
    py3-websockify \
    ttf-dejavu \
    x11vnc \
    xvfb

COPY rootfs /
RUN chmod a+x /etc/services.d/browser/run

EXPOSE 6080
