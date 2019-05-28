FROM php:5.6-fpm

RUN apt-get update && apt-get install -y

# Copy php.ini file
# I suspect the PHP extensons modify the php.ini file
COPY php.ini /usr/local/etc/php/php.ini

# Install PHP extensions
RUN pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install mysql