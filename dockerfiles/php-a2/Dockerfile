FROM php:7.2-apache

RUN \
    #upgrade all && install curl
    apt-get update && apt-get upgrade -y && apt-get install -y curl &&\
    #add docker repo
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer &&\
    #add node repo
    curl -sL https://deb.nodesource.com/setup_10.x | bash - &&\
    #add yarn repo
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list &&\
    #
    #upgrade all
    apt-get update && apt-get upgrade -y &&\
    #
    #install all
    apt-get install -y iputils-ping && \
    apt-get install -y zip unzip && \
    apt-get install -y git && \
    apt-get install -y nodejs && \
    apt-get install -y yarn && \
    docker-php-ext-install mysqli pdo pdo_mysql && \
    a2enmod rewrite

#add user inside image so we can run commands without sudo
RUN useradd --create-home --shell /bin/bash hk

#switch to created user
USER hk

#install composer speedup lib globally
RUN composer global require hirak/prestissimo

#switch back to root
USER root
