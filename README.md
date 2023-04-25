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
python manage.py runserver
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
