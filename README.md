# python-django-learning
Learning Django Framework

## Starting Django Project

### Create virtual environment and activate it

```shell
python3 -m venv env
source env/bin/activate 	
```

### Create requirements.txt file at root

```text
asgiref 
Django 
django-cors-headers 
djangorestframework 
djangorestframework-simplejwt 
PyJWT 
pytz 
sqlparse 
psycopg2-binary 
python-dotenv 
```

### install requirements

```shell
pip install -r requirements.txt
```

### Generate project directories and files

```shell
django-admin startproject backend
```

### Generate the api directory in backend

```shell
cd backend
python3 manage.py startapp api
```

### Open and configure settings.py
1. add imports

```python
from datetime import timedelta
from dotenv import load_dotenv
import os
```

2. add function that loads environment

```python
load_dotenv()
```

3. add environment variables
```python
ALLOWED_HOSTS = ["*"]

REST_FRAMEWORK = {
	"DEFAULT_AUTHENTIFICATION_CLASS": (
		"rest_framework_simplejwt.authentication.JWTAuthentication",
	),
	"DEFAULT_PERMISSION_CLASSES": [
		"rest_framework.permissions.IsAuthenticated",
	]
}

SIMPLE_JWT = {
	"ACCESS_TOKEN_LIFETIME": timedelta(minutes=30),
	"REFRESH_TOKEN_LIFETIME": timedelta(days=1),
}
```

4. add installed apps

```python
"api",
"rest_framework",
"corsheaders",
```

5. add middleware

```python
"corsheaders.middleware.CorsMiddleware",

```

6. add variable to bottom of file

```python
CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOWS_CREDENTIALS = True
```

### Move requirements.txt to backend directory leaving only env and backend at root.

```shell
mv requirements.txt \backend
```

### Make changes to configure JWT Authenticate/Authorization (See commit history for changes)

```shell
 api/serializers.py
 api/views.py 
 backend/urls.py 
```

### Migrate to be able to connect to database

```shell
python manage.py makemigrations
python manage.py migrate
```

### Run the application
```shell
python manage.py runserver
```

### Add custom api/models, api/serializers, api/views, api/urls
### Migrate DB Changes
### Add front-end

