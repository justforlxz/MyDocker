FROM alpine
MAINTAINER smounives <smounives@outlook.com>

RUN set -ex \
    && if [ $(wget -qO- ipinfo.io/country) == CN ]; then echo "http://mirrors.aliyun.com/alpine/latest-stable/main/" > /etc/apk/repositories ;fi \
    && apk --update add --no-cache libsodium py-pip \
    && pip --no-cache-dir install https://github.com/shadowsocksr/shadowsocksr/archive/manyuser.zip
RUN mkdir -p /etc/ssr
WORKDIR /etc/ssr

ENTRYPOINT ["/usr/bin/ssserver"]
CMD ssserver -c /etc/ssr/user-config.json
