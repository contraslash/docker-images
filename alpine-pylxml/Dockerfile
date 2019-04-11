FROM python:3.6-alpine

RUN apk update

RUN apk add --no-cache binutils gcc musl-dev autoconf libxml2-dev libxslt-dev

RUN pip install --no-cache-dir lxml==3.7.3

CMD ["python3"]
