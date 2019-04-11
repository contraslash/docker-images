FROM python:3.6-alpine

RUN apk update
RUN apk add --no-cache binutils gcc musl-dev  postgresql-dev

ENV PYTHONUNBUFFERED 1

RUN pip install --no-cache-dir  psycopg2 psycopg2-binary

CMD ["python3"]
