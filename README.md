# Local Web Development Environment

**Documentation is in-progress and incomplete!**

Deploy a web development environment for multiple domains running on different versions of PHP.

* Suitable as a local web development environment.
* Run multiple websites and browse to them by domain name.
* Access each website over HTTP and HTTPS. (SSL certificates are created during the build process.)
* Each website can use a different version of PHP.
* The stack uses CentOS, Apache and PHP-FPM.


## Initial Setup

After cloning the repository there are a few steps to setup and test the initial configuration.

Copy the contents from `/extra/hosts` and paste it into your local `hosts` file. This location varies depending on your operating system:

* Windows: C:\Windows\System32\drivers\etc\hosts
* Mac/Linux: /etc/hosts

Next, from your command line:
* Navigate to the `docker-compose-web-dev` folder.
* Run `docker-compose up`.
* Once the build finishes, open your browser and navigate to: http://php73.com
* You should see a page titled *HTML Test Page for /php73*.

The following domains should now be reachable through your web browser:

* http://php56.com
* https://php56.com

* http://php70.com
* https://php70.com

* http://php73.com
* https://php73.com


## Serving Your Website Files

Additional configuration is required to setup your local domains and serve the web files. First:

* Provide the directory path to your website files.

Then, for each website/domain create a new:
* Hosts file entry. This forwards the website domain to Apache.
* Vhosts entry. This tells Apache where your website files are located and which PHP version to use.

**Note:** Alternatively, you can copy your website files to the `/docker/www/` directory. In this case, you only need to add new vhost entries.

### Set Website Directory Path

Using the default setup Docker serves your web files from the `/docker/www/` directory. Each domain/website is in its own directory within this folder.

To change the directory location open the `/env` file and set a new `HTML_VOLUME` directory path. This should point to the dirctory containing your website files.

Each domain/website should be in its own directory similar to the directory structure in `/docker/www/`.

### Modify Vhost files

Apache uses the settings in your vhost files to serve your website. These settings configure:
* The domain name
* Access over HTTP and/or HTTPS
* Which files to serve
* PHP version

**TODO**

### Modify hosts file

Add a new entry in your vhosts file to access your website/domain locally.

```
127.0.0.1  loc.domain.com
:1  loc.domain.com
```

### Example Setup

Below is an example of how to setup the /env file and modify the vhosts and hosts files.

**TODO**


## Running the Environment

Navigate to the `docker-compose-web-dev` folder.

Start the environment with:
`docker-compose up`

Stop the environment with:
`ctrl-c` and then `docker-compose down`


## Connecting with your Web Browser
For HTTP connections use:
`http://localhost`

For HTTPS connections use:
`https://localhost` Your web browser will throw a certificate warning. Accept this risk to view the website.


## Website Files
Website files are mounted from the local file system at ./www into CentOS at /var/www/html/.

To show different website files modify the `HTML_VOLUME` variable in the ./.env file to point to your local website files.

## What Gets Built
Docker Compose builds several containers. There are also additional setup steps to help with web development, such as adding SSL and Xdebug support.

Docker containers:
* CentOS 7 with Apache 2.4
* PHP-FPM 5.6, 7.0, 7.3
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

HTTPS:
* 443

## Security Risks

There are security implications for how self-signed SSL certificates and MariaDB (root access) are setup which make this deployment unsuitable for production environments.
