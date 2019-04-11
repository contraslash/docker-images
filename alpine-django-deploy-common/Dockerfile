FROM python:3.7-alpine
RUN apk update
RUN apk add --no-cache linux-headers binutils gcc musl-dev mariadb-dev mariadb-client mysql-client build-base \
    jpeg-dev zlib-dev pcre-dev uwsgi uwsgi-python

ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install uwsgi

CMD ["python3"]
