:warning: WIP

# Yum Repository Server

Yum repository server accessible through a reverse proxy provided by nginx.

## Schema

![schema.png](.other/schema.png)

## Setup

#### Prerequisites

Instructions how to host this multicontainer application on a server with a specific domain name including SSL certificates.

#### Prerequisities

* domain name
* SSL certificate
* [docker-compose](https://docs.docker.com/compose)
    * [docker](https://docs.docker.com/engine)

#### Instructions

1. add your SSL certificate files to `nginx/conf.d/`
    * add your CRT file as `repository.crt`(`nginx/certs/repository.crt`)
    * add your KEY file as `repository.key`(`nginx/certs/repository.key`)
1. build the application via `docker-compose build`
1. start the application via `docker-compose up -d`
