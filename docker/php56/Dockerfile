FROM php:5.6.40-fpm

RUN apt-get update && apt-get install -y

# Copy php.ini file
# I suspect the PHP extensons modify the php.ini file
COPY php.ini /usr/local/etc/php/php.ini

# Install PHP extensions
# PHP 5.6 -> xdebug-2.5.5
RUN pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install mysql