FROM php:8.0.0-fpm-alpine

RUN apk update && apk add \
    curl \
    libzip-dev \
    icu-dev \
    libintl \
    libmcrypt-dev

RUN docker-php-ext-install pdo_mysql zip exif pcntl intl

RUN curl -sS https://getcomposer.org/installer | php -- --version=2.0.8 --install-dir=/usr/local/bin --filename=composer
