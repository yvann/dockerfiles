FROM alpine:3.3
MAINTAINER Yvann Boucher <yvann.boucher@gmail.com>

ENV S6_OVERLAY_VERSION 1.17.2.0

RUN set -x && \

    # s6 overlay

    apk add --no-cache --virtual .s6-overlay-build-deps curl ca-certificates && \
    curl -sSL "https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-amd64.tar.gz" | tar xvfz - -C / && \

    # cleaning

    apk del .s6-overlay-build-deps

ADD rootfs /
ENTRYPOINT ["/init"]
CMD []
