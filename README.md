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

1. Gunicorn WSGI serving Django CMS
2. Networked to PostgreSQL Database instance
3. Proxied to port 80 by NGINX webserver

## Usage

Go from localhost to the host you love most with one command

```bash
$ docker stack deploy -c docker-compose.yml cms
```

## Reference

- Minimal NGINX configuration for WSGI applications

  <https://nginx.org/en/docs/beginners_guide.html>

- Using NGINX as a reverse proxy over tcp

  <http://portainer.readthedocs.io/en/stable/faq.html>

- Deploying a simple python app (Flask) w/ Gunicorn and NGINX

  <http://flask.pocoo.org/docs/0.12/deploying/wsgi-standalone/#proxy-setups>

## TODO:

- [ ] Add relevant references from browser history on August 25-26
- [ ] Remove the line above when completed
- [ ] ~~Overwrite current https://github.com/retool-solutions/cms repo with this version, e.g.~~
        cp ~/Documents/GitHub/cms ~/Desktop/cms.bak
        
- [ ] Double check that script above before you run in HINT: it's wrong ;) #noseriously
