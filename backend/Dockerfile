FROM --platform=linux/amd64 python:3.10.9-slim-buster
LABEL maintainer="danylo.t@mate.academy"

WORKDIR /app


ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1


RUN pip install --upgrade pip
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
RUN pip install djangorestframework-simplejwt
RUN pip install drf_spectacular
RUN pip install django-debug-toolbar
RUN pip install psycopg2-binary
RUN pip install psycopg
RUN pip install pillow

COPY . .

RUN mkdir -p /vol/web/media

RUN adduser \
    --disabled-password \
    --no-create-home \
    django-user

RUN chown -R django-user:django-user /vol/
RUN chmod -R 755 /vol/web/

USER django-user