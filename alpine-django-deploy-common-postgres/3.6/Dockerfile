FROM python:3.6-alpine


LABEL maintainer="ma0c <ma0@contraslash.com>" \
    org.label-schema.name="Alpine Django Deploy Common Postgres" \
    org.label-schema.description="A base image to build Django images on top of Alpine Linux with Postgres" \
    org.label-schema.url="https://contraslash.com" \
    org.label-schema.vcs-url="https://github.com/contraslash/docker-images/tree/master/alpine-django-deploy-common-postgres"

RUN apk update && \
    apk add --no-cache --virtual .build-deps linux-headers binutils gcc musl-dev && \
    apk add --no-cache postgresql-dev uwsgi uwsgi-python3 && \
    LIBRARY_PATH=/lib:/usr/lib pip install --no-cache-dir psycopg2-binary==2.8.3 uwsgi==2.0.18 && \
    apk del .build-deps

CMD ["python3"]

