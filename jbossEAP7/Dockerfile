FROM jboss/base-jdk:8

MAINTAINER Francois Achache <francois.achache@gmail.com>

EXPOSE 8080 9990
ENV JBOSS_VERSION 7.0.0 
ENV JBOSS_HOME /opt/jboss/jboss-eap-7.0

ADD jboss-eap-$JBOSS_VERSION.tar.gz .

RUN $JBOSS_HOME/bin/add-user.sh -a demo demo -g USERR && $JBOSS_HOME/bin/add-user.sh admin admin

COPY deploy.sh $JBOSS_HOME/deploy.sh
COPY http-port.sh $JBOSS_HOME/http-port.sh

WORKDIR $JBOSS_HOME

CMD ["/opt/jboss/jboss-eap-7.0/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]




