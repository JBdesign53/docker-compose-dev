# Builds a Local Development Environment
Creates a local web development environment using Docker Compose and Docker.

A LAMP stack is built with CentOS, Apache and PHP. (MariaDB/MySQL can also be added. See Applications section below.)

SSL keys are also created for browsing over HTTPS.

## Applications
Core:
* CentOS 7
* Apache 2.4
* PHP 5.6
* MySQL - Disabled. See the /docker-compose.yml file and uncomment to enable.

Additional setup and packages:
* SSL keys using OpenSSL
* Nano
* Xdebug

## Images
The following Docker images are used:
* centos/httpd-24-centos7
* php:5.6.40-fpm
* mariadb:10.4.2

## Running
Starting the environment:
`docker-compose up`

Stopping the environment:
`ctrl-c` and then `docker-compose down`

## Website Files
Web files are mounted from the local file system into /var/www/etc/. Modify the file path in /.env.
