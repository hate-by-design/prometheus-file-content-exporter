FROM python:3.6-buster

RUN pip --no-cache-dir install pyyaml python-json-logger prometheus_client

COPY . /

ENV EXPORTER_PORT=9111
ENV EXPORTER_CONFIG=/config.yaml

EXPOSE 9111

CMD ["python", "/main.py"]
