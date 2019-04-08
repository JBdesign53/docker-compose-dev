# LAMP Web Development Environment
Creates a LAMP stack for local web development with Docker Compose. The stack uses CentOS, Apache and PHP-FPM.

Self-signed SSL keys are created for browsing over HTTPS. See the Applications section below for a full list of additional setup activities.

MariaDB/MySQL is turned off by default. See the Applications section below for instructions on enabling MariaDB.

## Containers and Additional Setup

Docker Compose builds several containers and also performs additional setup activities for web development, such as adding SSL and Xdebug support.

Containers:
* CentOS 7 with Apache 2.4
* PHP-FPM 5.6
* MariaDB - Disabled by default. To enable, uncomment lines in the /docker-compose.yml file.

Additional installation and setup:
* SSL keys using OpenSSL
* Nano
* Xdebug 2.5.5

## Docker Images
The following Docker images are used:
* centos/httpd-24-centos7
* php:5.6.40-fpm
* mariadb:10.4.2

## Website Files
Web files are mounted from the local file system into /var/www/etc/ in CentOS. Modify the file path in /.env to point to your local website files.

## Running the Environment
Start the environment:
`docker-compose up`

Stop the environment:
`ctrl-c` and then `docker-compose down`

## Connecting with your Web Browser
For HTTP connections use:
`http://localhost`

For HTTPS connections use:
`https://localhost` Your web browser will throw a certificate warning. Accept this risk to view the website.

You can use a hosts file hack to use a different domain. For example, you could add the following line into your hosts file to connect at `loc.example.com`:

`loc.example.com  127.0.0.1`

## Ports
The following ports are exposed by Apache:
* 80(HTTP)
* 8080 (HTTP)
* 443 (HTTPS)
* 8443 (HTTPS)
