FROM python:3.7-alpine

MAINTAINER ma0c <ma0@contraslash.com>

LABEL maintainer="ma0c <ma0@contraslash.com>" \
    org.label-schema.name="Alpine Django Deploy Common" \
    org.label-schema.description="A base image to build Django images on top of Alpine Linux" \
    org.label-schema.url="https://contraslash.com" \
    org.label-schema.vcs-url="https://github.com/contraslash/docker-images/tree/master/alpine-django-deploy-common-s3"

RUN apk update && \
    apk add --no-cache --virtual .build-deps linux-headers binutils gcc musl-dev zlib-dev pcre-dev build-base && \
    apk add mariadb-dev mariadb-client  jpeg-dev uwsgi uwsgi-python3 libffi-dev && \
    LIBRARY_PATH=/lib:/usr/lib pip install --no-cache-dir \
        uwsgi==2.0.18 boto3==1.9.130 django-storages==1.7.1 cryptography==2.6.1 mysqlclient==1.4.2 && \
    apk del .build-deps

CMD ["python3"]
