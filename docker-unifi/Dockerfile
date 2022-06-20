FROM ubuntu:20.04
LABEL maintainer="hez.km.ua"
LABEL version="0001"
LABEL description="UNIFI"

#ENV unifi 

#Install latest patches
RUN apt-get -y update \
    && apt-get -y install ca-certificates \
    && apt-get -y install apt-transport-https \
    && apt-get -y install wget


CMD echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
CMD wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ui.com/unifi/unifi-repo.gpg

RUN apt-get -y update &&\
    apt-get -y install unifi

#    rm -rf /var/lib/apt/lists/* &&\
#    apt clean

EXPOSE 8443 3478