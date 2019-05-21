FROM php:7.0-fpm

RUN apt-get update && apt-get install -y

# Copy php.ini file
# I suspect the PHP extensons modify the php.ini file
COPY php.ini /usr/local/etc/php/php.ini

# Install PHP extensions
# PHP 7 -> xdebug-2.7.0
RUN pecl install xdebug-2.6.0 \
    && docker-php-ext-enable xdebug

# Returns an error
# RUN docker-php-ext-install mysqli