FROM php:7.2

ARG HOST_USER_UID=1000
ARG HOST_USER_GID=1000

RUN groupadd -g $HOST_USER_GID notroot \
    && useradd -lm -u $HOST_USER_UID -g $HOST_USER_GID notroot

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxml2-dev \
        libpq-dev \
        wget \
        git

RUN docker-php-ext-install \
  gd \
  json \
  mbstring \
  xml \
  xmlrpc \
  opcache \
  pgsql \
  pdo \
  pdo_pgsql

RUN mkdir /root/.ssh
RUN touch /root/.ssh/config
RUN echo "Host *" >> /root/.ssh/config
RUN echo "    StrictHostKeyChecking no" >> /root/.ssh/config
RUN chmod 400 /root/.ssh/config

RUN mkdir /home/notroot/.ssh
RUN chown notroot /home/notroot/.ssh

RUN touch /home/notroot/.ssh/config
RUN echo "Host *" >> /home/notroot/.ssh/config
RUN echo "    StrictHostKeyChecking no" >> /home/notroot/.ssh/config
RUN chmod 400 /home/notroot/.ssh/config
RUN chown notroot /home/notroot/.ssh/config



RUN curl -sS https://getcomposer.org/installer | php -- --version=1.6.5 --install-dir=/usr/local/bin --filename=composer
RUN composer --version

VOLUME ["/app"]
WORKDIR /app

