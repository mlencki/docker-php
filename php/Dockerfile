FROM php:8.0.0-fpm-alpine

ARG COMPOSER_VERSION

RUN apk --no-cache update \
    && apk --no-cache upgrade \
    && apk add --no-cache --virtual \
        .build-deps \
        $PHPIZE_DEPS \
        gcc \
        g++ \
        autoconf \
        tar \
    && apk add --no-cache \
        icu-dev \
        libintl \
        libmcrypt-dev \
    && NPROC=$(getconf _NPROCESSORS_ONLN) \
    && docker-php-ext-install -j${NPROC} mysqli pdo pdo_mysql intl  \
    && pecl install -o -f redis \
    && docker-php-ext-enable redis \
    && curl -sS https://getcomposer.org/installer | php -- --version=${COMPOSER_VERSION} --install-dir=/usr/local/bin --filename=composer \
    && apk del --no-cache gcc g++ .build-deps