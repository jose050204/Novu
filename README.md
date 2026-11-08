# Novu - Create New Connections

> The project was deployed at https://novu.cat (**no longer online**).

Novu is a Tinder-like web app to find new friendships with other students.

It includes technologies such as **facial scanning for ID verification**, used to check that the ID submitted by a user actually belongs to a real person.

## Prerequisites

- Python 3.13 and package dependencies
- Django 6.0.4+
- MySQL DBMS with a database named `novudb` already created (we used [Laragon](https://laragon.org/) during development)
- Angular 19

## Technologies Used

### Frontend

- **Angular** - official page [here](https://v19.angular.dev/overview).
- **Tailwind CSS** - official page [here](https://tailwindcss.com/).

> [!IMPORTANT]
> For the frontend to work as intended, locate the `src/app/baseURLconfig.ts` file and set the `development` variable to `true`:
>
> ```ts
> // inside src/app/baseURLconfig.ts
> development = true
> ```
>
> This facilitates the deployment process.

### Backend

- **Django**

> [!IMPORTANT]
> To try the chat functionality, you must run the Django server with **Daphne** instead of Django's own development server. See Daphne's documentation [here](https://docs.djangoproject.com/en/6.0/howto/deployment/asgi/daphne/).
>
> Note that images might not work when using Daphne to run the Django server locally.

## Starting the Project

To run the project you need a database named `novudb`, as specified in the `db.conf` file inside the `novu/novu` folder of the Django project.

### 1. Starting the Backend

Make sure you have:

- The MySQL Server running
- A database named `novudb`
- A user with permissions over that database
- A Python virtual environment

#### Database setup

Open your MySQL Shell and create the user and grant permissions:

```sql
-- user creation
CREATE USER 'novu'@'localhost' IDENTIFIED BY 'BDnovu3';

-- permissions
GRANT ALL ON novudb.* TO 'novu'@'localhost';
```

If the database has not been created yet:

```sql
CREATE DATABASE novudb;
```

#### Python virtual environment

Create the virtual environment:

```bash
python -m venv /path/to/new/virtual/environment
```

Activate it. On Windows:

```bash
./path/to/new/virtual/environment/Scripts/activate
```

The prompt will now display `(venv)` at the beginning.

#### Install dependencies

Locate the `requirements.txt` file and run:

```bash
pip install -r requirements.txt
```

#### Run migrations

> [!WARNING]
> You must run the migrations before starting Django, otherwise an exception will occur.

Run these commands inside the folder where `manage.py` is located.

Create the migrations:

```bash
python ./manage.py makemigrations
```

Apply the migrations:

```bash
python ./manage.py migrate
```

If the migrations fail to apply, double-check that:

- The MySQL Server is running
- A database named `novudb` exists
- The configured user has the appropriate permissions

### 2. Starting the Frontend

First, install all Node.js packages:

```bash
npm install
```

Then start the frontend:

```bash
ng serve -o
```
