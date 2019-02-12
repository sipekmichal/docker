FROM debian:jessie

LABEL maintainer="mich.sipek@gmail.com"

ADD local_policy.jar /opt/
ADD US_export_policy.jar /opt/
RUN echo deb "http://http.debian.net/debian jessie-backports main" >>/etc/apt/sources.list.d/backports.list && \
    echo "CET" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata && \    
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install vim dnsutils telnet software-properties-common redis-tools wget -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes java-common && \
    wget https://d3pxv6yz143wms.cloudfront.net/java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb && \
    dpkg --install java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb  && \
    rm -rf java-1.8.0-amazon-corretto-jdk_8.192.12-2_amd64.deb && \
    apt-get clean  && \
    rm -rf /var/lib/apt/lists/* && \
    mv /opt/*.jar /usr/lib/jvm/java-1.8.0-amazon-corretto/jre/lib/security/

VOLUME /etc/timezone:/etc/localtime

ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-amazon-corretto

CMD ["/bin/bash"]
