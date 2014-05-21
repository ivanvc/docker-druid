FROM dockerfile/java

MAINTAINER Ivan Valdes <ivan@vald.es>

# Supervisor
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

# confd
RUN wget -q https://github.com/kelseyhightower/confd/releases/download/v0.3.0/confd_0.3.0_linux_amd64.tar.gz -O /tmp/confd_0.3.0.tar.gz
RUN tar zxf /tmp/confd_0.3.0.tar.gz && mv confd /usr/bin/confd
RUN mkdir -p /etc/confd/conf.d
RUN mkdir -p /etc/confd/templates

# Druid
RUN wget -q http://static.druid.io/artifacts/releases/druid-services-0.6.105-bin.tar.gz -O /tmp/druid-services.tar.gz
RUN tar xfz /tmp/druid-services.tar.gz -C /opt
RUN mv /opt/druid-services* /opt/druid-services

# Add files
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD confd/runtime.properties.tmpl /etc/confd/templates/runtime.properties.tmpl
ADD confd/kafka.toml /etc/confd/conf.d/kafka.toml
