FROM ubuntu:20.04
LABEL maintainer="hez.km.ua"
LABEL version="0001"
LABEL description="UNIFI"

#ENV unifi 

#Install latest patches
RUN apt-get -y update \
    && apt-get -y install ca-certificates \
    && apt-get -y apt-transport-https \
    && apt-get -y wget


CMD echo 'deb https://www.ui.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list
CMD wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ui.com/unifi/unifi-repo.gpg

RUN apt-get -y update \
    && apt-get -y install unifi


# Install nginx, php-fpm and supervisord from ubuntu repository
RUN apt install -y nginx php-fpm && \
rm -rf /var/lib/apt/lists/* && apt clean

#Define the ENV variable
ENV nginx_vhost /etc/nginx/sites-available/default
ENV php_conf /etc/php/7.4/fpm/php.ini
ENV nginx_conf /etc/nginx/nginx.conf

# Enable PHP-fpm on nginx virtualhost configuration
COPY default ${nginx_vhost}
RUN sed -i -e 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' ${php_conf} && echo "\ndaemon off;" >> ${nginx_conf}


