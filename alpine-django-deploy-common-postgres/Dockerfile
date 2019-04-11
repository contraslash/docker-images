FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache linux-headers binutils gcc musl-dev postgresql-dev uwsgi uwsgi-python

ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install --no-cache-dir  psycopg2 psycopg2-binary uwsgi

CMD ["python3"]
