# Axolotl

This is Basic `Django` Project developed from the django official documentation

Here the Documentation [Link](https://docs.djangoproject.com/en/4.0/intro/tutorial01/)

## Prerequisites
* [Python 3.10+](https://www.python.org/downloads/)
* [PostgreSQL 14](https://github.com/Antony-M1/docker-postgresql)

## Create the environment
```
python3.10 -m venv env
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
