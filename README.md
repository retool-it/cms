---
title: cms
author: Zachary Wilson
date: 2017-08-26T00:00:00.000Z
---

# CMS

A containerized content management system (CMS) w/ PostgreSQL backend.

## Install

```
git clone https://github.com/retool-solutions/cms
```

## Prerequisites

1. [Docker CE](https://docs.docker.com/engine/installation/#supported-platforms)
2. `docker-compose`
3. `.env` file

## Usage

```bash
$ docker-compose up -d
```

You'll need to migrate to the new postgres db

```bash
$ docker-compose exec cms python manage.py migrate
```

Then create a new superuser

```bash
$ docker-compose exec cms python manage.py createsuperuser
```

Open <http://localhost:8000> to log in w/ the superuser username and password and begin creating content.

## Example `.env` file

```
POSTGRES_PASSWORD=changeme
POSTGRES_USER=admin
POSTGRES_DB=djangocms
POSTGRES_PORT=5432
SECRET_KEY=secretkey
DEBUG=True
ALLOWED_HOSTS=*
DB_HOST=db
```
