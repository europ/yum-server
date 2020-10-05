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

1. add your desired packages (RPM files) to `yum/packages/`
1. add your SSL certificate files to `nginx/certs/`
    * add your CRT file as `repository.crt`(`nginx/certs/repository.crt`)
    * add your KEY file as `repository.key`(`nginx/certs/repository.key`)
1. build the application via `docker-compose build`
1. start the application via `docker-compose up -d`

## Customization

#### Repository

Edit the `yum/repository.repo` file to change the name and ID of the repository to yours.

#### Enable HTTP

Note that using HTTP is **not** secure!

To enable HTTP change the HTTP part in `nginx/conf.d/repository.conf` file to:

```
# HTTP
server {
    listen 80;
    listen [::]:80;

    # this is the internal Docker DNS, cache only for 30s
    resolver 127.0.0.11 valid=30s;

    location / {
        set $upstream http://yum:80;
        proxy_pass $upstream;
        proxy_set_header Host $host;
    }
}
```
