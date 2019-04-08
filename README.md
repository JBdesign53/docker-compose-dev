# LAMP Web Development Environment
Creates a LAMP stack for local web development with Docker Compose. The stack uses CentOS, Apache and PHP-FPM.

Self-signed SSL keys are created for browsing over HTTPS. See the 'What Gets Built' section below for a full list of additional setup activities.

MariaDB/MySQL is turned off by default. See the 'What Gets Built' section below for instructions on enabling MariaDB.

## Running the Environment
Start the environment with:
`docker-compose up`

Stop the environment with:
`ctrl-c` and then `docker-compose down`

## Connecting with your Web Browser
For HTTP connections use:
`http://localhost`

For HTTPS connections use:
`https://localhost` Your web browser will throw a certificate warning. Accept this risk to view the website.

To use a domain other than `//localhost` you will need to modify your 'hosts' file. For example, you could add the following lines into your hosts file to connect to the URL `loc.example.com`:

```
127.0.0.1  loc.example.com
:1  loc.example.com
```

## Website Files
Web files are mounted from the local file system at ./www into /var/www/etc/ in CentOS. The local volume is set in the /.env file.

Modify the file path in ./.env to point to your local website files.

## What Gets Built

Docker Compose builds several containers and also performs additional setup activities to help with web development, such as adding SSL and Xdebug support.

Containers:
* CentOS 7 with Apache 2.4
* PHP-FPM 5.6
* MariaDB - Disabled by default. To enable, uncomment lines in the /docker-compose.yml file.

Additional installation and setup:
* SSL keys using OpenSSL
* Xdebug 2.5.5
* Nano

## Security Risks

There are security implications for how self-signed SSL certificates and MariaDB (root access) are setup which make this deployment unsuitable for production environments.

## Docker Images
The following Docker images are used:
* centos/httpd-24-centos7
* php:5.6.40-fpm
* mariadb:10.4.2

## Ports
The following ports are exposed by Apache and Docker Compose:
* 80(HTTP)
* 8080 (HTTP)
* 443 (HTTPS)
* 8443 (HTTPS)
