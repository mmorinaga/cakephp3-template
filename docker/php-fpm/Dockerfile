FROM php:7.3-fpm

ENV DEBIAN_FRONTEND noninteractive

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt-get update && apt-get install -y git zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

RUN docker-php-ext-install pdo pdo_mysql

# Install memcached
RUN apt-get install -y libz-dev libmemcached-dev
RUN pecl install memcached
RUN docker-php-ext-enable memcached
# Install extensions
RUN apt-get update && apt-get install -y \
        libmcrypt-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libicu-dev \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd exif
RUN pecl install mcrypt && docker-php-ext-enable mcrypt
# Install xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-install mysqli
