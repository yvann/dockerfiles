FROM yvann/alpine-s6-base:latest
MAINTAINER Yvann Boucher <yvann.boucher@gmail.com>

ENV CONSUL_DOMAIN consul.service.consul
ENV CONSUL_PORT 8500

ENV CONSUL_TEMPLATE_VERSION 0.14.0
ENV CONSUL_TEMPLATE_SHA256 7c70ea5f230a70c809333e75fdcff2f6f1e838f29cfb872e1420a63cdf7f3a78

RUN set -x && \

    # consul-template

    apk add --no-cache --virtual .consul-template-build-deps curl ca-certificates unzip && \
    curl -sSL "https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip" -o consul-template.zip && \
    echo "${CONSUL_TEMPLATE_SHA256}  consul-template.zip" | sha256sum -c && \
    mkdir -p /bin && \
    unzip consul-template.zip -d /bin && \
    rm -f consul-template.zip && \
    addgroup consul-template && \
    adduser -g "" -D -H -s /bin/sh -G consul-template consul-template && \

    # cleaning

    apk del .consul-build-deps .consul-template-build-deps

ADD rootfs /
ENTRYPOINT ["/init"]
CMD []
