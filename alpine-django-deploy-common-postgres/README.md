# Alpine Django Deploy Common

A minimal [Alpine Linux](https://alpinelinux.org/) Docker Image with the essential to deploy a common django project, that includes
[psycopg2-binary](https://pypi.org/project/psycopg2-binary/) and [uWSGI](https://pypi.org/project/uWSGI/).

## Usage

A proposed base `Dockerfile` for a django application

```dockerfile
FROM contraslash/alpine-django-deploy-common:latest

RUN mkdir /code
WORKDIR /code
ADD requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt

ADD . /code/

EXPOSE 8000

CMD ["uwsgi", "--ini", "uwsgi.ini"]

```

Remember to use the exact same version in your requirements.txt file

```text
psycopg2-binary==2.8.3
uwsgi==2.0.18 
```

`uswgi.ini` is a uWSGI configuration file example and the entry point should be something like

```ini
[uwsgi]
module=django_project_name.wsgi:application
master=True
pidfile=/tmp/project-master.pid
vacuum=True
max-requests=5000
http=:8000
processes=3
harakiri=20
single-interpreter=True
enable-threads=True
buffer-size=32768
```

## Local building

```bash
docker build -t contraslash/alpine-django-deploy-common-postgres .
```

## Contributing

Feel free to make an issue in the [Github Repository](https://github.com/contraslash/docker-images)
or send a mail to [Mauricio Collazos](mailto:ma0@contraslash.com)
