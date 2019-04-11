FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache binutils gcc musl-dev mariadb-dev mariadb-client mysql-client

ENV PYTHONUNBUFFERED 1

RUN pip install mysqlclient

CMD ["python3"]
