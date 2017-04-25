FROM python:3.6-alpine
RUN apk update
RUN apk add build-base
RUN apk add jpeg-dev
RUN apk add zlib-dev
ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install pillow

CMD ["python3"]
