# Alpine Django Deploy Common

A minimal Alpine Linux Docker Image with the essential to deploy a common django project, that include Mysql, Pillow and uWSGI to deploy.

`uswgi.ini` is a uWSGI configuration file example and the entry point shuld be something like

```
CMD ["uwsgi", "--ini", "uwsgi.ini"]
```
