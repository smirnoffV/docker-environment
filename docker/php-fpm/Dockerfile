FROM php:7.2-fpm

# set container project directory absolute path
WORKDIR /var/www/bulletin-board.loc

# install some extensions
RUN apt-get update -y && apt-get install -y sendmail libpng-dev geoip-database-extra geoip-bin

# install pdo, gd, bcmath
RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install gd \
    && docker-php-ext-install bcmath

# install php-redis
RUN pecl install redis \
    && docker-php-ext-enable redis

#install xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

#copy xdebug config into container
COPY ./xdebug.ini /usr/local/etc/php/conf.d/

RUN usermod -u 1000 www-data