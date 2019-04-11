FROM contraslash/alpine-django-deploy-common
RUN apk update
RUN apk add --no-cache build-base jpeg-dev zlib-dev
ENV LIBRARY_PATH=/lib:/usr/lib

ENV PYTHONUNBUFFERED 1

RUN pip install --no-cache-dir pillow

CMD ["python3"]
