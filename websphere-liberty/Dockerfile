FROM websphere-liberty:javaee7

MAINTAINER Francois Achache <francois.achache@gmail.com>

EXPOSE 9080
ENV WEBSPHERE_VERSION 4.1.1.162
ENV WEBSPHERE_HOME /



COPY deploy.sh $WEBSPHERE_HOME/deploy.sh
COPY http-port.sh $WEBSPHERE_HOME/http-port.sh

WORKDIR $WEBSPHERE_HOME


