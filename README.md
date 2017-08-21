---
title: CMS
author: Zachary Wilson
date: 2017-08-20T00:00:00.000Z
---

# cms

Content Management System based on Django CMS

## Features

- Django CMS
- Postgres SQL Database
- Docker!

## Installation

Create an `.env` file in the root of the project dir containing the following

```.ini
# secret key can't be empty
SECRET_KEY='secretkey'
# use '*' for all hosts
ALLOWED_HOSTS=['*']
POSTGRES_PASSWORD=changeme
POSTGRES_DB=db_name
POSTGRES_USER=db_username
POSTGRES_PORT=5432
PYTHONHASHSEED=random
```

Replace the placeholder values with desired/required info

Start docker compose

```
docker-compose up -d
```

Run the following command in the app service's container

```
docker-compose run app python manage.py migrate
docker-compose exec python manage.py createsuperuser
```

Follow the prompts to create a super user.

Open your browser and navigate to <http://localhost:8000> and login with the username/password created in the previous step.

> ⚠️ Keep in mind that the database you create won't travel with your application image so don't do to much work on the front end that you don't want to lose.

## Running as a service

When you're ready to deploy your application run

```
docker stack deploy -c docker-cloud.yml cms
```

## Todo

- [ ] Verify stack configuration against [Django Deployment Checklist](https://docs.djangoproject.com/en/1.11/howto/deployment/checklist/)
    - [X] `SECRET_KEY` must be a large random value and it must be kept secret.
    - [ ] You must never enable debug in production.
    - [ ] If you use a wildcard, you must perform your own validation of the Host HTTP header, or otherwise ensure that you aren’t vulnerable to this category of attacks
    - [X] Database passwords are very sensitive. You should protect them exactly like SECRET_KEY.
    - [ ] To use different sender addresses, modify the `DEFAULT_FROM_EMAIL` and `SERVER_EMAIL` settings.
    - [ ] In production, you must define a `STATIC_ROOT` directory where `collectstatic` will copy them.
    - [ ] Make sure your web server never attempts to interpret \[media files\].
    - [ ] Your web server must redirect all HTTP traffic to HTTPS, and only transmit HTTPS requests to Django.
    - [X] Enabling persistent database connections can result in a nice speed-up when connecting to the database accounts for a significant part of the request processing time.
    - [ ] Enabling the cached template loader often improves performance drastically, as it avoids compiling each template every time it needs to be rendered.
    - [ ] Review your logging configuration before putting your website in production, and check that it works as expected as soon as you have received some traffic.
    - [X] invoke the Python process running your Django application using the `-R` option or with the `PYTHONHASHSEED` environment variable set to random.
