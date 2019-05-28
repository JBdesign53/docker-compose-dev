FROM php:7.0-fpm

RUN apt-get update && apt-get install -y

# Copy php.ini file
# I suspect the PHP extensons modify the php.ini file
COPY php.ini /usr/local/etc/php/php.ini

# Install PHP extensions
RUN pecl install xdebug-2.6.0 \
    && docker-php-ext-enable xdebug

# Install mysqli
RUN docker-php-ext-install mysqli \
    && docker-php-ext-enable mysqli