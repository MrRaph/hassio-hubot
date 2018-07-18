# Setup base system
ARG BUILD_ARCH=amd64

ARG BUILD_FROM=hassioaddons/ubuntu-base-${BUILD_ARCH}:2.0.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

RUN apt-get update && \
    apt-get install -y nodejs npm jq && \
    npm install -g yo generator-hubot && \
    mkdir -p /data/hubot /root/.config/insight-nodejs && \
    chmod g+rwx /root /root/.config /root/.config/insight-nodejs

WORKDIR /data/hubot

RUN yo hubot --owner="Hubot HomeAssistant" --name="Hubot" --adapter=slack

COPY external-scripts.json /data/hubot/external-scripts.json
COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]
