FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache linux-headers binutils gcc musl-dev mariadb-dev mariadb-client mysql-client build-base jpeg-dev \
  zlib-dev pcre-dev uwsgi uwsgi-python libffi-dev

ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install --no-cache-dir uwsgi==2.0.17 boto3==1.9.20 django-storages==1.7.1 cryptography==2.3.1

CMD ["python3"]
