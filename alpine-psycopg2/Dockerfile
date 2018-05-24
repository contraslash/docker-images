FROM python:3.6-alpine

RUN apk update
RUN apk add --no-cache binutils
RUN apk add --no-cache gcc
RUN apk add --no-cache musl-dev
RUN apk add --no-cache postgresql-dev

ENV PYTHONUNBUFFERED 1

RUN pip install psycopg2
RUN pip install psycopg2-binary

CMD ["python3"]
