FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache linux-headers
RUN apk add --no-cache binutils
RUN apk add --no-cache gcc
RUN apk add --no-cache musl-dev
RUN apk add --no-cache mariadb-dev
RUN apk add --no-cache mariadb-client
RUN apk add --no-cache mysql-client
RUN apk add --no-cache build-base
RUN apk add --no-cache jpeg-dev
RUN apk add --no-cache zlib-dev
RUN apk add --no-cache pcre-dev
RUN apk add --no-cache uwsgi
RUN apk add --no-cache uwsgi-python

ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

CMD ["python3"]
