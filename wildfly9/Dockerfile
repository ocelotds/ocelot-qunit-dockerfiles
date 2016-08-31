FROM jboss/base-jdk:8

MAINTAINER Francois Achache <francois.achache@gmail.com>

EXPOSE 8080 9990
ENV WILDFLY_VERSION 9.0.2.Final
ENV JBOSS_HOME /opt/jboss/wildfly

RUN cd $HOME && curl http://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz | tar zx \
	&& mv $HOME/wildfly-$WILDFLY_VERSION $HOME/wildfly

RUN $JBOSS_HOME/bin/add-user.sh -a demo demo -g USERR && $JBOSS_HOME/bin/add-user.sh admin admin

COPY deploy.sh $JBOSS_HOME/deploy.sh
COPY http-port.sh $JBOSS_HOME/http-port.sh

WORKDIR $JBOSS_HOME

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
