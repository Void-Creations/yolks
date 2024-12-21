# ----------------------------------
# Environment: MongoDB
# ----------------------------------
FROM --platform=$TARGETOS/$TARGETARCH mongo:4-focal

LABEL author="Michael Parker " maintainer="parker@pterodactyl.io"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y apt-transport-https ca-certificates wget gnupg2 \
    && apt-key del 656408E390CFB1F5 || true \
    && wget -qO - https://pgp.mongodb.com/server-4.4.asc | apt-key add - \
    && apt-get update -y \
    && apt-get install -y netcat-openbsd iproute2 \
    && useradd -d /home/container -m container -s /bin/bash

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]