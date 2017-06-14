FROM python:3.6-alpine

RUN apk update

RUN apk add --no-cache binutils
RUN apk add --no-cache gcc
RUN apk add --no-cache musl-dev
RUN apk add --no-cache autoconf
RUN apk add --no-cache libxml2-dev
RUN apk add --no-cache libxslt-dev

RUN pip install lxml==3.7.3

CMD ["python3"]
