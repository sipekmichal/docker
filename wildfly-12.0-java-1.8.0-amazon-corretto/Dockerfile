FROM sipekmichal/debian-openjdk8-amazon-corretto

LABEL maintainer="mich.sipek@gmail.com"

ENV JBOSS_HOME=/opt/wildfly
ENV REFRESHED_AT="20109-06-10 14:34"
ARG DEBIAN_FRONTEND=noninteractive

RUN wget http://download.jboss.org/wildfly/12.0.0.Final/wildfly-12.0.0.Final.tar.gz && \
tar -xvzf wildfly-12.0.0.Final.tar.gz && \
mv wildfly-12.0.0.Final /opt/wildfly &&\
rm wildfly-12.0.0.Final.tar.gz && \
/opt/wildfly/bin/add-user.sh admin Admin461 --silent && \
mkdir -p /opt/wildfly/modules/com/oracle/main/ && \
mkdir /opt/upload && \
addgroup --system --gid 251 jboss && \
adduser --system --ingroup jboss --uid 251 --disabled-login --home /opt/wildfly --shell /bin/false wildfly && \
chown -R wildfly:jboss /opt/wildfly && \
chown wildfly:jboss /opt/upload

USER wildfly

ADD ojdbc7*.jar /opt/wildfly/modules/com/oracle/main/
ADD module.xml /opt/wildfly/modules/com/oracle/main/
ADD standalone.xml /opt/wildfly/standalone/configuration/

EXPOSE 8080 9990

CMD ["/opt/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
