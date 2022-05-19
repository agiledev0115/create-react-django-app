# create-react-django-app

Minimal Django + PostgreSQL + Create React App template

## What's included?

### Frontend

- TypeScript (frontend language)
- React (frontend framework)
  - Create React App (support for TSX, ES6, TypeScript, no need to install bundler, ...etc)
  - An example fetch() GET request to the server in the `client/src/App.tsx`

### Backend

- Poetry (Python dependency management system)
- Python3 (backend language)
  - Black (formatter)
- Django (backend framework)
  - Django REST Framework (Django's toolkit for building Web APIs)
  - An example app in the `server/exampleApp` folder showing how to setup API models, serializers, and views
- PostgreSQL (database)
  - Psycopg (PostgreSQL adapter for Python)

## Getting Started

Clone this repository to your local machine:

```bash
git clone https://github.com/kevinshen56714/create-react-django-app.git
```

### Client

In the project folder,

```bash
cd client
yarn && yarn start
```

### Server

#### PostgreSQL

To run the server, you first need to have [PostgreSQL](https://www.postgresql.org/download/) installed and running. You need to create a user and a database, and enter your information in the DATABASES section of `server/main/settings.py`. It may look something like this:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "your-db-name",
        "USER": "your-user",
        "PASSWORD": "your-password",
        "HOST": "localhost",
        "PORT": "5432",
        # You can instead use the following OPTIONS if you have the files set up
        # see more at https://docs.djangoproject.com/en/4.0/ref/databases/#postgresql-notes
        # "OPTIONS": {
        #     "service": "my_service",
        #     "passfile": ".my_pgpass",
        # },
    }
}
```

#### Poetry

In addition to the database, you need to setup the Python environment. We use [poetry](https://python-poetry.org/docs/#installation) for dependency management, so poetry needs to be installed first. Once installed, in the project folder,

```bash
poetry shell  # this should create a virtualenv for you at .venv
poetry install
cd server
python manage.py migrate  # make sure your selected Python interpreter is the one in .venv
python manage.py runserver
```

Once the server is running, you can go to localhost:8000/customer/, localhost:8000/customer/create to play around with the example API GET and POST requests.
