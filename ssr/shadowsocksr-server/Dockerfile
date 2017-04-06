#
# Dockerfile for ShadowsocksR
#

FROM ubuntu:16.04
MAINTAINER kirigaya kazushin <kirigaya@mkacg.com>

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        supervisor \
        git \
    && rm -rf /var/lib/apt/lists/* \
    && cd /opt \
    && git clone -b manyuser https://github.com/breakwa11/shadowsocks.git 

COPY init.sh /init.sh
COPY user-config.json /opt/shadowsocks/
COPY supervisord.conf /etc/supervisor/
COPY services.conf /etc/supervisor/conf.d/

EXPOSE 8888

ENTRYPOINT ["/init.sh", "/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
