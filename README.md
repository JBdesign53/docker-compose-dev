# LAMP Web Development Environment
Deploy a web development environment for multiple domains running different versions of PHP. Suitable as a local development environment using HTTP and HTTPS. The stack uses CentOS, Apache and PHP-FPM.

Self-signed SSL keys are created for browsing over HTTPS. See the 'What Gets Built' section below for a full list of additional setup activities.

MariaDB/MySQL is turned off by default. See the 'What Gets Built' section below for instructions on enabling MariaDB.

Document:
* Local hosts file
* Vhosts - http/https
* Environment variables and WWW files
* Firefox SSL self-signed certificate bug

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

Note: If you are using a domain other than `//localhost` you do not need to change the OpenSSL setup. Although the SSL keys are created using 'localhost' as the domain name other domain names should work correctly.

## Website Files
Website files are mounted from the local file system at ./www into CentOS at /var/www/html/.

To show different website files modify the `HTML_VOLUME` variable in the ./.env file to point to your local website files.

## What Gets Built
Docker Compose builds several containers. There are also additional setup steps to help with web development, such as adding SSL and Xdebug support.

Docker containers:
* CentOS 7 with Apache 2.4
* PHP-FPM 5.6
* MariaDB - Disabled by default. To enable, uncomment lines in the /docker-compose.yml file.

Additional setup steps and installation:
* SSL keys using OpenSSL
* Xdebug 2.5.5
* Nano

## Docker Images
The following Docker images are used:
* centos/httpd-24-centos7
* php:5.6.40-fpm
* mariadb:10.4.2

## Ports
The following ports are exposed by Apache and Docker Compose:

HTTP:
* 80
* 8080

HTTPS:
* 443
* 8443

## Security Risks

There are security implications for how self-signed SSL certificates and MariaDB (root access) are setup which make this deployment unsuitable for production environments.
