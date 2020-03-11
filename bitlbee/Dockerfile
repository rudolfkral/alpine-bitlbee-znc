#
# Bitlbee (w/ Facebook and OTR) + Alpine Linux
#

FROM alpine:edge

#RUN echo "@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories && \
#    apk --update add ca-certificates bitlbee@testing bitlbee-facebook@testing bitlbee-otr@testing bitlbee-libpurple@testing && \
#    adduser -h /var/lib/bitlbee -s /sbin/nologin -DH bitlbee && \
#    chown -R bitlbee:bitlbee /var/lib/bitlbee && \
#    touch /var/run/bitlbee.pid && \
#    chown bitlbee:bitlbee /var/run/bitlbee.pid && \
#    rm -rf /var/cache/apk/*

RUN apk --update add libgcrypt-dev glib-dev gnutls-dev libpurple pidgin-dev autoconf automake libtool json-glib-dev git libwebp-dev build-base python3 && \
    cd /tmp && \
    wget http://get.bitlbee.org/src/bitlbee-3.5.1.tar.gz && \
    tar xf bitlbee-3.5.1.tar.gz && \
    cd bitlbee-3.5.1 && \
    export PYTHON=python3 && \
    ./configure --purple=1 --plugins=1 --skype=1 && \
    make && \
    make install && \
    make install-dev && \
    cd .. && \
    git clone https://github.com/bitlbee/bitlbee-facebook.git && \
    cd bitlbee-facebook && \
    ./autogen.sh && \
    make && \
    make install && \
    cd .. && \
    git clone --recursive https://github.com/majn/telegram-purple && \
    cd telegram-purple && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    git clone https://github.com/dylex/slack-libpurple && \
    cd slack-libpurple && \
    make && \
    make install && \
    cd .. && \
    mkdir /var/lib/bitlbee && \
    adduser -h /var/lib/bitlbee -s /sbin/nologin -DH bitlbee && \
    chown -R bitlbee:bitlbee /var/lib/bitlbee && \
    touch /var/run/bitlbee.pid && \
    chown bitlbee:bitlbee /var/run/bitlbee.pid && \
    rm -rf /var/cache/apk/*

USER bitlbee
VOLUME ["/var/lib/bitlbee"]
EXPOSE 6667/tcp

ENTRYPOINT ["bitlbee", "-F", "-n", "-v"]

# libgcrypt-dev
# glib-dev
# gnutls-dev
# libpurple-dev
# pidgin-dev
# autoconf
# automake
# libtool
# json-glib-dev
# git
# libwebp-dev
# apk add python3 & potem del
# apk add build-base & potem del


# bitlbee:
# PYTHON=python3 ./configure --purple=1 --plugins=1 --skype=1
# wget && cd && make & make install & make install-dev
# bitlbee facebook
# git && cd && ./autogen.sh && make && make install
# bitlbee telegram
# git && cd &&  ./configure && make && make install

