ARG IMAGE_VERSION=3.9

FROM python:${IMAGE_VERSION}

ENV PYTHONUNBUFFERED 1

WORKDIR /usr/app

COPY requirements.txt /usr/app/requirements.txt

RUN apt-get update \
    && pip install --upgrade pip \
    && pip install -r requirements.txt

COPY docker-entrypoint.sh /user/app/scripts

ADD . .

EXPOSE 8000