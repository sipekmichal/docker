FROM bitnami/minideb:jessie

LABEL maintainer="mich.sipek@gmail.com"

ADD https://d3pxv6yz143wms.cloudfront.net/8.232.09.1/java-1.8.0-amazon-corretto-jdk_8.232.09-1_amd64.deb ./

RUN echo "CET" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata && \
    mkdir -p /usr/share/man/man1 && touch /usr/share/man/man1/javac.1.dpkg-tmp && \    
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes java-common && \
    dpkg --install java-1.8.0-amazon-corretto-jdk_8.232.09-1_amd64.deb  && \
    rm -rf java-1.8.0-amazon-corretto-jdk_8.232.09-1_amd64.deb && \
    apt-get clean all  && \
    rm -rf /var/lib/apt/lists/*

VOLUME /etc/timezone:/etc/localtime

ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-amazon-corretto

CMD ["/bin/bash"]
