FROM ubuntu:22.04

LABEL author="Timothy Leung <timothy@springracks.com>" maintainer="Timothy Leung <timothy@springracks.com>"
ARG DEBIAN_FRONTEND=noninteractive
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'

RUN apt-get update -y && \
    apt-get install -y tzdata curl wget ca-certificates software-properties-common apt-transport-https fontconfig locales openssl git tar sqlite iproute2 python3 && \
    echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen en_US.UTF-8 && \
    add-apt-repository -y ppa:openjdk-r/ppa && \
    apt-get update -y && \
    apt-get install -y openjdk-8-jre openjdk-11-jre openjdk-16-jre openjdk-17-jre openjdk-18-jre openjdk-19-jre && \
    rm -rf /var/lib/apt/lists/*

RUN ln -s /usr/lib/jvm/java-8-openjdk-$(dpkg --print-architecture)/jre/bin/java /usr/local/bin/java8 && \
    ln -s /usr/lib/jvm/java-11-openjdk-$(dpkg --print-architecture)/bin/java /usr/local/bin/java11 && \
    ln -s /usr/lib/jvm/java-16-openjdk-$(dpkg --print-architecture)/bin/java /usr/local/bin/java16 && \
    ln -s /usr/lib/jvm/java-17-openjdk-$(dpkg --print-architecture)/bin/java /usr/local/bin/java17 && \
    ln -s /usr/lib/jvm/java-18-openjdk-$(dpkg --print-architecture)/bin/java /usr/local/bin/java18 && \
    ln -s /usr/lib/jvm/java-19-openjdk-$(dpkg --print-architecture)/bin/java /usr/local/bin/java19 && \
    useradd -d /home/container -m container

USER container
ENV USER=container HOME=/home/container

WORKDIR /home/container

COPY ./prompt.py /prompt.py
COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]
