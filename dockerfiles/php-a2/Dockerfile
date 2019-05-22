FROM php:7.2-apache

RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y git

RUN apt-get install zip unzip

RUN docker-php-ext-install mysqli pdo pdo_mysql

RUN apt-get install -y curl
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

RUN useradd --create-home --shell /bin/bash hk

USER hk
RUN composer global require hirak/prestissimo

USER root