FROM python:3.6-alpine
RUN apk update
RUN apk add binutils
RUN apk add gcc
RUN apk add mariadb-dev
RUN apk add mariadb-client
RUN apk add mysql-client
RUN apk add musl-dev

ENV PYTHONUNBUFFERED 1

RUN pip install mysqlclient

CMD ["python3"]
