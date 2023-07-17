FROM php:8.0-fpm as php

# Install libs, extensions, and baseline PHP needs
RUN apt-get update && apt-get install -y \
    git \
    libfreetype6-dev libjpeg62-turbo-dev \
    libpng-dev \
    libssl-dev autoconf \
    ca-certificates curl libicu-dev \
    imagemagick libonig-dev \
    libmagickwand-dev default-mysql-client libzip-dev\
    && \
    pecl install imagick \
    && \
    docker-php-ext-install \
    bcmath \
    gd mbstring opcache \
    zip pdo_mysql intl \
    && \
    docker-php-ext-enable imagick

RUN pecl install mailparse && docker-php-ext-enable mailparse && echo "Added mailparse.so to php.ini"

# Install the composer tool
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

# Copy in server configuration
COPY ./docker/php/php.ini /usr/local/etc/php
COPY ./docker/php/www.conf /usr/local/etc/php-fpm.d

# Copy over source files
COPY --chown=www-data:www-data ./html /var/www/html

# Composer install
RUN composer install -d /var/www/html/ && \
    chown -R www-data:www-data /var/www/html/vendor && \
    chown -R www-data:www-data /var/www/html/composer.lock


