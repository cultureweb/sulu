FROM php:7.4-apache

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

RUN apt-get update \
    && apt-get install -y --no-install-recommends locales apt-utils git libicu-dev g++ libpng-dev libxml2-dev libzip-dev libonig-dev libxslt-dev;

RUN apt-get -y update && apt-get install -y wget gnupg

RUN curl -fsSL https://deb.nodesource.com/setup_12.x | bash

RUN apt-get install -y \
zip \
unzip \
mcrypt \
zlib1g-dev \
libgmp-dev \
libpng-dev \
nodejs \
libfontconfig1 \
libxrender1 \
&& pecl install apcu \
&& docker-php-ext-install -j$(nproc) pdo_mysql \
&& ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/include/gmp.h \
&& docker-php-ext-install -j$(nproc) gmp \
zip \
opcache

RUN docker-php-ext-install mbstring

RUN docker-php-ext-install zip

RUN docker-php-ext-install gd

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -  && \
echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

# Install Composer
RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
   mv composer.phar /usr/local/bin/composer

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/xdebug.ini \
	&& echo extension=apcu.so > /usr/local/etc/php/conf.d/apcu.ini

COPY xdebug_state.sh /usr/bin/xdebug_state

WORKDIR /var/www/html