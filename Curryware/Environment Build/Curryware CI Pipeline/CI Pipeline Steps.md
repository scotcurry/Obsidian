Run tests:
- python3 -m unittest -v tests.test_xml_parser (need to figure out how to check for bad status codes)

- Build the container:

```syntax=docker/dockerfile:1

FROM python:3.8-slim-buster

# Uncomment these when building a local container, but comment them when building a container for deployment.

# This tells the docker container to make this port available to the host

ENV LISTEN_PORT=8080

EXPOSE 8080

WORKDIR /app

COPY requirements.txt requirements.txt

RUN pip3 install -r requirements.txt

COPY . .

RUN useradd appuser && chown -R appuser /app

USER appuser

CMD exec ddgunicorn -b :8080 --workers 1 --threads 8 --timeout 0 app:app`

```

- You can also run the command directly:
`DD_SERVICE="currywareff" DD_ENV="prod" DD_LOGS_INJECTION=true ddtrace-run gunicorn -b :8080 --workers 1 --threads 8 --timeout 0 app:app `