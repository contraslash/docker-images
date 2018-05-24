FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache linux-headers
RUN apk add --no-cache binutils
RUN apk add --no-cache gcc
RUN apk add --no-cache musl-dev
RUN apk add --no-cache postgresql-dev
RUN apk add --no-cache uwsgi
RUN apk add --no-cache uwsgi-python

ENV PYTHONUNBUFFERED 1

RUN pip install psycopg2
RUN pip install psycopg2-binary

ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install uwsgi

CMD ["python3"]
