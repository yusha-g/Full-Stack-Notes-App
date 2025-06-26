# Django-React Fullstack Notes App
A full‑stack web application built with Django (REST API) and React (frontend). Users can register, log in, and manage personal notes.

## Features
- [ ] User Authentication (register/login via JWT)
- [ ] CRUD operations on notes
- [ ] React frontend with protected routes
- [ ] Django REST API backend
- [ ] Dockerized setup with docker-compose

## Tech Stack
Backend: Django, Django REST Framework, SimpleJWT

Frontend: React, React Router, Axios, JWT-Decode

Containerization: Docker, Docker Compose

## Step-by-Step Guide
### Setup Django Project
- `django-admin startproject backend`
- in backend, create an app called `api` using `python manage.py startapp api`

#### Settings.py
```

from datetime import timedelta
from dotenv import load_dotenv
import os

load_dotenv()

...


ALLOWED_HOSTS = ["*"]

REST_FRAMEWORK = {
    "DEFAULT_AUTHENTICATION_CLASSES": (
        "rest_framework_simplejwt.authentication.JWTAuthentication",
    ),
    "DEFAULT_PERMISSION_CLASSES": [
        "rest_framework.permissions.IsAuthenticated",
    ],
}

SIMPLE_JWT = {
    "ACCESS_TOKEN_LIFETIME": timedelta(minutes=30),
    "REFRESH_TOKEN_LIFETIME": timedelta(days=1),
}

...


INSTALLED_APPS = [
    ...
    'api',
    'rest_framework',
    'corsheaders',
]

...


MIDDLEWARE = [
    ...
    'corsheaders.middleware.CorsMiddleware',
]

...


DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOW_CREDENTIALS = True
```
