#Dockerfile
#MySql Server
From mysql

MAINTAINER Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

ENV MYSQL_ROOT_PASSWORD password

RUN -d -name dstack-mysql

RUN apt-get update

RUN mysql -u root -ppassword -h 127.0.0.1 -P 3308 -e CREATE DATABASE dbtest

RUN apt-get install vim -y

Volume 
      ./docker/www:/app:delegated
      ./docker/php/php.ini:/opt/docker/php/etc/conf.d/php.ini:ro

#Apache Server
From Ubuntu

MAINTAINER Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN -d -name dstack-apache

RUN apt-get update
RUN apt-get -q -y install apache2

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

RUN mkdir -p /var/lock/apache2 /var/run/apache2

EXPOSE 80

VOLUME       
      ./docker/www:/app:delegated
      ./docker/apache/my_vhost.conf:/vhosts/myapp.conf:ro
      ./docker/apache/certs:/certs

CMD /bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"

#Redis Server
FROM redis

MAINTAINER Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN -d -name dstack-redis

ENV DATABASE_HOST=host.docker.internal

#PHP Server
FROM php

MAINTAINER Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN -d -name dstack-php

VOLUME
      - ./docker/www:/app:delegated
      - ./docker/apache/my_vhost.conf:/vhosts/myapp.conf:ro
      - ./docker/apache/certs:/certs

FROM phpmyadmin

MAINTAINER Sarah Schmid und Muriel Ruegg <schmidsarah21@gmail.com>

RUN -d -name dstack-phpmyadmin

EXPOSE 81

ENV DATABASE_HOST=host.docker.internal
