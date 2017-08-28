---
title: cms
author: Zachary Wilson
date: 2017-08-26T00:00:00.000Z
---

# CMS

A lightweight, ready-to-deploy, containerized content management system and "production-ready" stack environment implementing recommended deployment best practices.

## Install

```
git clone https://github.com/retool-solutions/cms
```

## Features

Docker Containers!

1. [Gunicorn](http://gunicorn.org) WSGI serving Django CMS
2. Networked to [PostgreSQL](http://postgresql.org) Database instance
3. Proxied to port 80 by [NGINX](http://nginx.org) webserver

## Prerequisites

1. [Docker CE](https://docs.docker.com/engine/installation/#supported-platforms)
2. AWS EC2 instance [created w/ `docker-machine`](https://docs.docker.com/machine/drivers/aws/#custom-ami-and-ssh-username)

## Usage

Go from localhost to the host you love most.

```bash
$ eval $(docker-machine env production)
$ docker stack deploy -c docker-compose.yml stack
```

--------------------------------------------------------------------------------

## Deploying

I'm working on making deployment happen w/o manual intervention. For now, there are a few manual steps required before deploying this stack to a server for the first time, namely:

1. NGINX configuration file must exist either in the image or on the server where the containers will be deployed
2. After deploying the stack, you must migrate your django db and create a new superuser to log into the admin site

These are described in further detail below.

### Prep

Copy `./config/nginx/default.conf` to the server

```bash
$ cd ./config/nginx
$ docker-machine scp default.conf production:~
$ docker-machine ssh production docker config create default.conf /users/home/ubuntu/default.conf
```

Where `server` is the name of the production server.

### Deploy

Deploy the stack

```bash
eval (docker-machine env production)
docker stack deploy -c docker-compose.yml stack
```

Migrate your db

```bash
docker exec stack_app_1 python manage.py migrate
```

Create a new superuser

```bash
docker exec -it stack_app_1 python manage.py createsuperuser
```

## Reference

- Minimal NGINX configuration for WSGI applications

  <https://nginx.org/en/docs/beginners_guide.html>

- Using NGINX as a reverse proxy over tcp

  <http://portainer.readthedocs.io/en/stable/faq.html>

- Deploying a simple python app (Flask) w/ Gunicorn and NGINX

  <http://flask.pocoo.org/docs/0.12/deploying/wsgi-standalone/#proxy-setups>

- Docker compose version 3 file reference

  <https://docs.docker.com/compose/compose-file>

- Building python images

  <https://hub.docker.com/_/python/>

- Integrating PostgreSQL db

  <https://hub.docker.com/_/postgres/>
