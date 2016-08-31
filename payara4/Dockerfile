FROM java:openjdk-8-jdk

MAINTAINER Francois Achache <francois.achache@gmail.com>

ENV PAYARA_VERSION 4.1.1.162
ENV PAYARA_HOME /usr/local/payara41

RUN apt-get update && apt-get install -y curl unzip zip inotify-tools && rm -rf /var/lib/apt/lists/* \
  && curl -L -o /tmp/payara-$PAYARA_VERSION.zip https://s3-eu-west-1.amazonaws.com/payara.co/Payara+Downloads/Payara+$PAYARA_VERSION/payara-$PAYARA_VERSION.zip \
  && unzip /tmp/payara-$PAYARA_VERSION.zip -d /usr/local \
  && rm -f /tmp/payara-$PAYARA_VERSION.zip

RUN $PAYARA_HOME/bin/asadmin start-domain domain1 \
  && echo "AS_ADMIN_USERPASSWORD=demo" > pwd.txt \
  && $PAYARA_HOME/bin/asadmin create-file-user --passwordfile=pwd.txt --groups USERGP demo \
  && $PAYARA_HOME/bin/asadmin stop-domain domain1 \
  && rm pwd.txt

EXPOSE 8080 4848 8181

COPY deploy.sh $PAYARA_HOME/deploy.sh
COPY http-port.sh $PAYARA_HOME/http-port.sh

WORKDIR $PAYARA_HOME

CMD /usr/local/glassfish4/bin/asadmin start-domain --verbose domain1


