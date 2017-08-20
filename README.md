# cms

Content Management System based on Django CMS

# Features

- Django CMS
- Postgres SQL Database
- Docker!


# Installation

Create an `.env` file in the root of the project dir containing the following

```.ini
# secret key can't be empty
SECRET_KEY='secretkey'
# use '*' for all hosts
ALLOWED_HOSTS=['localhost']
POSTGRES_PASSWORD=changeme
POSTGRES_DB=db_name
POSTGRES_USER=db_username
POSTGRES_PORT=5432
```

Replace the placeholder values with desired/required info

Start docker compose

    docker-compose up -d

Run the following command in the app service's container

    docker-compose run app python manage.py migrate
    docker-compose exec python manage.py createsuperuser

Follow the prompts to create a super user.

Open your browser and navigate to <http://localhost:8000> and login with the username/password created in the previous step.
