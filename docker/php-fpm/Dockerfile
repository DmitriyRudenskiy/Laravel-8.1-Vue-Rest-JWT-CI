FROM php:8.0-fpm-alpine
MAINTAINER Dmitriy Rudenskiy <dmitriy.rudenskiy@gmail.com>

RUN set -xe && apk add --update --no-cache git openssh-client mariadb-client

# fix: No such file or directory
RUN set -xe && apk add --update --no-cache libbz2 libpng-dev libwebp libjpeg-turbo libxpm freetype

RUN set -ex; \
    apk add --no-cache --virtual .build-deps \
    zlib-dev \
    bzip2-dev \
    freetype-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    libwebp-dev \
    libzip-dev \
    libxpm-dev; \
    docker-php-ext-configure gd --with-freetype=/usr --with-jpeg=/usr --with-webp=/usr --with-xpm=/usr; \
    docker-php-ext-install bz2 gd mysqli pdo pdo_mysql; \
    apk del .build-deps

# install xdebug 3.0
RUN git clone --depth 1 https://github.com/xdebug/xdebug.git /usr/src/php/ext/xdebug \
    && docker-php-ext-configure xdebug --enable-xdebug-dev \
    && docker-php-ext-install xdebug \
    && mkdir /tmp/debug

# Copy xdebug configuration for remote debugging
COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini


