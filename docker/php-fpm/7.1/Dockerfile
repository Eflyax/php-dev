FROM ubuntu:16.04

MAINTAINER Eflyax

RUN apt-get clean && apt-get update

RUN apt-get -y install locales
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get install -y software-properties-common
RUN add-apt-repository -y ppa:ondrej/php
RUN apt-get update
RUN apt-get install -y php7.1-fpm php7.1-cli php7.1-mcrypt php7.1-gd php7.1-mysql
RUN apt-get install -y php7.1-mysql php7.1-imap php7.1-mbstring php7.1-xml
RUN apt-get install -y php7.1-sqlite

RUN apt-get remove -y --purge software-properties-common
COPY ./conf/www.conf /etc/php/7.1/fpm/pool.d/www.conf
COPY ./conf/php.ini /etc/php/7.1/mods-available/php.ini

RUN ln -s /etc/php/7.1/mods-available/php.ini /etc/php/7.1/cli/conf.d/90-php.ini && \
    ln -s /etc/php/7.1/mods-available/php.ini /etc/php/7.1/fpm/conf.d/90-php.ini && \
    mkdir -p /run/php

RUN  usermod -u 1000 www-data

WORKDIR /var/www/

CMD ["php-fpm7.1"]

EXPOSE 9000

# cleanup
USER root
RUN apt-get clean && \
	rm -rfv \
	/tmp/* \
	/var/lib/apt/lists/* \
	/var/tmp/*
