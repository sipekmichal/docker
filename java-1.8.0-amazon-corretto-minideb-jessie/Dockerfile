FROM bitnami/minideb:jessie

LABEL maintainer="mich.sipek@gmail.com"

RUN echo deb "http://http.debian.net/debian jessie-backports main" >>/etc/apt/sources.list.d/backports.list && \
    echo "CET" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata && \
    mkdir -p /usr/share/man/man1 && touch /usr/share/man/man1/javac.1.dpkg-tmp && \    
    apt-get update && apt-get install wget -y && apt-get install java-common -y && \
    DEBIAN_FRONTEND=noninteractive && \
    wget https://d3pxv6yz143wms.cloudfront.net/java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb && \
    dpkg --install java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb  && \
    rm -rf java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb && \
    apt-get clean  && \
    rm -rf /var/lib/apt/lists/*

VOLUME /etc/timezone:/etc/localtime

ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-amazon-corretto

CMD ["/bin/bash"]
