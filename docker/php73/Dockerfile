FROM php:7.3.3-fpm

RUN apt-get update && apt-get install -y

# Copy php.ini file
# I suspect the PHP extensons modify the php.ini file
COPY php.ini /usr/local/etc/php/php.ini

# Change the port number of PHP-FPM
# COPY zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf

# Install PHP extensions
# PHP 7 -> xdebug-2.7.0
#RUN pecl install xdebug-2.7.0 \
#    && docker-php-ext-enable xdebug

#RUN docker-php-ext-install mysqli