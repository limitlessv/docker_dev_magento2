# Docker files for setup development env for magento2

A Composer package to setup magento 2 development enviroments with PHPStorm and docker
 

The composer package **limitlessv/docker_dev_magento2** deploys docker infrastructure defintion files such as [docker-compose.yml](docker-compose.yml) to your Magento 2 root folder and enables you to host your Magento 2 shops without having to install Apache/Nginx, MySQL or PHP on your system.


## Package Name


`limitlessv/docker_dev_magento2`

(fork of arvatoscm/dockerize-magento2)


## Software Requirements

For Linux users you must have a recent version of [docker](https://github.com/docker/docker/releases) and [docker-compose](https://github.com/docker/compose/releases) installed.

If you are a Mac or Windows user, use the [Docker Toolbox](https://www.docker.com/products/docker-toolbox).

## Installation

Add `limitlessv/docker_dev_magento2` to your existing Magento 2 shop:

```bash
composer require --ignore-platform-reqs limitlessv/docker_dev_magento2
chmod +x bin/console
```

This will place some files in your Magento root:

- `docker-compose.yml`
The docker infrastructure definition
- `bin/console`
A utility script for controlling dockerized Magento projects
- `config`
A folder which contains the configuration files for PHP, Nginx and phpMyAdmin


## Usage

`dockerize-magento2` comes with `bin/console` script that can be used to install Magento and to execute Magentos' bin/magento script inside the PHP docker container:

Trigger the Magento 2 installation process:

```bash
bin/console install <hostname>
```

Start the docker containers:

```bash
bin/console start
```

Stop the docker containers:

```bash
bin/console stop
```

Execute `bin/magento` inside the docker container:

```bash
bin/console exec [arguments]
```

For more information on how to use docker-compose visit: https://docs.docker.com/compose/

## Configuration

The `install` action depends on some parameters such as usernames and passwords. We have put in some default values for you that will work for a quick test:

```
DATABASE_NAME="limitlessv_magento2"
DATABASE_USER="limitlessV"
DATABASE_PASSWORD="enAVINa2"
DATABASE_ROOT_PASSWORD="enAVINa2"

ADMIN_USERNAME="adm_user"
ADMIN_FIRSTNAME="Admin"
ADMIN_LASTNAME="MyStore"
ADMIN_EMAIL="example@example.com"
ADMIN_PASSWORD="enAVINa2"

DEFAULT_LANGUAGE="en_US"
DEFAULT_CURRENCY="USD"
DEFAULT_TIMEZONE="Etc/UTC"

BACKEND_FRONTNAME="admin"
```

If you want to use different parameters change the values in the [.env](.env) file to your needs.
After customizing the parameters just run trigger the installation with `bin/console install <hostname>`.

## Licensing

dockerize-magento2 is licensed under the Apache License, Version 2.0.
See [LICENSE](LICENSE) for the full license text.
