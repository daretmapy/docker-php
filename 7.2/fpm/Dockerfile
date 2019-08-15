FROM php:7.2-fpm

ARG HOST_USER_UID=1000
ARG HOST_USER_GID=1000

RUN groupadd -g $HOST_USER_GID notroot \
    && useradd -lm -u $HOST_USER_UID -g $HOST_USER_GID notroot

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxml2-dev \
        libpq-dev

RUN docker-php-ext-install \
  gd \
  json \
  mbstring \
  xml \
  xmlrpc \
  opcache \
  pgsql \
  pdo \
  pdo_pgsql \
  zip

WORKDIR /var/www/html