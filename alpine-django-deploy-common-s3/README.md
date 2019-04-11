# Alpine Django Deploy Common with S3

A minimal Alpine Linux Docker Image with the essential to deploy a common django project, that include Mysql, uWSGI and boto3 and django-storagesto deploy.

`uswgi.ini` is a uWSGI configuration file example and the entry point shuld be something like

```
CMD ["uwsgi", "--ini", "uwsgi.ini"]
```

## Local building

```bash
docker build -t contraslash/alpine-django-deploy-common-s3 .
docker push 

```