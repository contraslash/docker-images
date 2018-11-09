# Alpine Django Deploy Common with S3 and Phantom

A minimal Alpine Linux Docker Image with the essential to deploy a common django project, that include Mysql, uWSGI and boto3 and django-storages and Phantom JS to generate PDF.

To build a local version 
```bash 
docker build -t contraslash/alpine-django-deploy-common-s3-phantom .
```