FROM python:3.6-alpine

LABEL maintainer="ma0c <ma0@contraslash.com>" \
    org.label-schema.name="Alpine Django Deploy Common" \
    org.label-schema.description="A base image to build Django images on top of Alpine Linux" \
    org.label-schema.url="https://contraslash.com" \
    org.label-schema.vcs-url="https://github.com/contraslash/docker-images/tree/master/alpine-django-deploy-common"

RUN apk update && \
    apk add --no-cache --virtual .build-deps linux-headers binutils gcc musl-dev build-base zlib-dev pcre-dev && \
    apk add --no-cache mariadb-dev mariadb-client jpeg-dev  uwsgi uwsgi-python3 && \
    LIBRARY_PATH=/lib:/usr/lib pip install --no-cache-dir uwsgi==2.0.18 mysqlclient==1.4.2 && \
    apk del .build-deps

CMD ["python3"]
