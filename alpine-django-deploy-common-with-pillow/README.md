# Alpine Django Deploy Common with Pillow

A minimal [Alpine Linux](https://alpinelinux.org/) Docker Image with the essential to deploy a common django project, 
that include [mysqlclient](https://pypi.org/project/mysqlclient/) and [uWSGI](https://pypi.org/project/uWSGI/) and [Pillow](https://pypi.org/project/Pillow/).
## Usage

A proposed base `Dockerfile` for a django application

```dockerfile
FROM contraslash/alpine-django-deploy-common:python3.7

RUN mkdir /code
WORKDIR /code
ADD requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt

ADD . /code/

EXPOSE 8000

CMD ["uwsgi", "--ini", "uwsgi.ini"]

```

Remember tu use the exact same version in your requirements.txt file

```text
mysqlclient==1.4.2 
pillow==6.0.0
uwsgi==2.0.18 

```

`uswgi.ini` is a uWSGI configuration file example and the entry point should be something like

```
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

Also this image uses mysql so, remember to create a database

```sql
CREATE DATABASE ${project_name};
CREATE USER ${project_name}_user identified by '${random_password}';
GRANT ALL PRIVILEGES ON ${project_name}.* to ${project_name}_user;
FLUSH PRIVILEGES;
```

## Local building

```bash
docker build -t contraslash/alpine-django-deploy-common-with-pillow .
```

## Contributing

Feel free to make an issue in the [Github Repository](https://github.com/contraslash/docker-images)
or send a mail to [Mauricio Collazos](mailto:ma0@contraslash.com)