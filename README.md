# Axolotl

This is Basic `Django` Project developed from the django official documentation

Here the Documentation [Link](https://docs.djangoproject.com/en/4.0/intro/tutorial01/)

## Prerequisites

- [Python 3.10+](https://www.python.org/downloads/)
- [PostgreSQL 14](https://github.com/Antony-M1/docker-postgresql)

## Create the environment

```
python3.10 -m venv env
```
Activate the Environment

For Linux/mac
```
source env/bin/activate
```

For Windows
```
source env\Scripts\activate
```

Install all the requirements

```
pip install -r requirements.txt
```

## Create a database

Make sure you already created a databse in postgresql

If your running database in `docker`.

To access the databse container

```
docker exec -it -u postgres <CONTAINER_NAME> psql
```

Create Database

```
CREATE DATABASE <DB_NAME>;
```

Example `username` and `password` but its `Not Recommended` for the `Production`.

**Username: `postgres`**

**Password: `postgres`**

URI:

```
jdbc:postgresql://localhost:5432/axolotl
```

![image](https://user-images.githubusercontent.com/96291963/234267158-3898de90-6530-4f75-8ce2-a9fd847e8b23.png)

# .env

Create a `.env` file in the root directory and add the following details

```
SECRET_KEY=<YOUR_SECRET_KEY>
ALLOWED_HOSTS=<LIST_OF_ALLOWED_HOST>

# Database Connection
DATABASES_ENGINE=django.db.backends.postgresql
DATABASES_NAME=<YOUR_DATABASE_NAME>
DATABASES_USER=<YOUR_DATABASES_USER>
DATABASES_PASSWORD=<YOUR_DATABASES_PASSWORD>
DATABASES_HOST=<YOUR_DATABASES_HOST>
DATABASES_TEST=<YOUR_DATABASES_TEST>
```

## Django CMD

Create Project

```
django-admin startproject <PROJECT_NAME>
```

Run Project

```
python manage.py runserver <CUSTOM_PORT>
```

Run Project in custom port default is `8000` if you want to change it in `8080` chage the number

If you want to change the server’s IP, pass it along with the port. For example, to listen on all available public IPs (which is useful if you are running Vagrant or want to show off your work on other computers on the network), use:

`python manage.py runserver 0:8000`

0 is a shortcut for 0.0.0.0. Full docs for the development server can be found in the [runserver](https://docs.djangoproject.com/en/4.0/ref/django-admin/#django-admin-runserver) reference.

```
python manage.py runserver <CUSTOM_PORT>
```
Create `APP`
```
python manage.py startapp <APP_NAME>
```

Create Tables
```
python manage.py migrate
```
Make Migrations
```
python manage.py makemigrations <APP_NAME>
```
*Note: if you are not mentioning the app name it will run for all the app what you mentioned in the `INSTALLED_APPS`*

There’s a command that will run the migrations for you and manage your database schema automatically - that’s called [migrate](https://docs.djangoproject.com/en/4.0/ref/django-admin/#django-admin-migrate), and we’ll come to it in a moment - but first, let’s see what SQL that migration would run. The [sqlmigrate](https://docs.djangoproject.com/en/4.0/ref/django-admin/#django-admin-sqlmigrate) command takes migration names and returns their SQL:
```
python manage.py sqlmigrate <APP_NAME> 0001
```
The `sqlmigrate` command doesn’t actually run the migration on your database - instead, it prints it to the screen so that you can see what SQL Django thinks is required. It’s useful for checking what Django is going to do or if you have database administrators who require SQL scripts for changes.

[Check Project Health](https://docs.djangoproject.com/en/4.0/ref/django-admin/#django-admin-check)
```
python manage.py check
```
this checks for any problems in your project without making migrations or touching the database.

Create Table From migration files
```
python manage.py migrate
```
The `migrate` command takes all the migrations that haven’t been applied (Django tracks which ones are applied using a special table in your database called `django_migrations`) and runs them against your database - essentially, synchronizing the changes you made to your models with the schema in the database.

making model changes:
* Change your models (in models.py).
* Run `python manage.py makemigrations` to create migrations for those changes
* Run `python manage.py migrate` to apply those changes to the database.

To invoke the Python shell, use this command:
```
python manage.py shell
```
We’re using this instead of simply typing “python”, because `manage.py` sets the `DJANGO_SETTINGS_MODULE` environment variable, which gives Django the Python import path to your `mysite/settings.py` file.

Once you’re in the shell, explore the `database API` using shell.

**Creating an admin user**
```
python manage.py createsuperuser
```

**Running tests**
```
python manage.py test <APP_NAME>
```

# Debugger for VS-code
Create a file in root directory of the project `.vscode/launch.json`
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Django",
            "type": "python",
            "request": "launch",
            "program": "${workspaceFolder}/manage.py",
            "args": [
                "runserver"
            ],
            "django": true,
            "justMyCode": true
        }
    ]
}
```
