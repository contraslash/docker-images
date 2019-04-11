FROM python:3.6-alpine
RUN apk update
RUN apk add --no-cache build-base jpeg-dev zlib-dev
ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install --no-cache-dir pillow

CMD ["python3"]
