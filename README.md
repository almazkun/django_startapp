# django_startapp
Django start a new project and app

# Project structure

Usually I would like to have the following structure for the new Django Project:
```bash
tree django_project
├── apps
│  ├── accounts
│  │  ├── migrations
│  │  │  ├── 0001_initial.py
│  │  │  └── __init__.py
│  │  ├── __init__.py
│  │  ├── admin.py
│  │  ├── apps.py
│  │  ├── forms.py
│  │  ├── models.py
│  │  ├── tests.py
│  │  └── views.py
│  └── __init__.py
├── main
│  ├── migrations
│  │  └── __init__.py
│  ├── __init__.py
│  ├── admin.py
│  ├── apps.py
│  ├── models.py
│  ├── tests.py
│  └── views.py
├── settings
│  ├── __init__.py
│  ├── asgi.py
│  ├── settings.py
│  ├── urls.py
│  └── wsgi.py
├── LICENSE
├── Pipfile
├── Pipfile.lock
├── README.md
├── db.sqlite3
└── manage.py
```

But always have to google how to do it.

1. Create folders, files, project and apps:
```bash
mkdir django_project
cd django_project
pipenv install django && pipenv shell
django-admin startproject settings .

python3 manage.py startapp main 

# stat app command when called with `destination` will NOT create a directory,
# but will populate all the files needed for the app in the `destination` directory.
mkdir -p apps/accounts
touch apps/__init__.py
python3 manage.py startapp accounts ./apps/accounts
```
2. Change the `apps/accounts/apps.py` file `name` to `apps.accounts`:
```py
class AccountsConfig(AppConfig):
    default_auto_field = "django.db.models.BigAutoField"
    name = "apps.accounts" # This line is changed
```
3. Change the `settings/settings.py` file `INSTALLED_APPS` to include the new app:
```py
INSTALLED_APPS = [
    ...
    "main.apps.MainConfig", # `main` will also be ok
    "apps.accounts.apps.AccountsConfig", # `apps.accounts` will also be ok
]



