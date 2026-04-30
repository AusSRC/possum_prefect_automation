FROM python:3.10-slim

# Fix BOTH possible apt source locations with https to workaround the firewall
RUN sed -i 's|http://deb.debian.org|https://deb.debian.org|g' \
      /etc/apt/sources.list /etc/apt/sources.list.d/* 2>/dev/null || true

RUN pip install --no-cache-dir prefect==3.4.25 \ 
 && apt-get update \
 && apt-get install -y git postgresql-client ca-certificates curl \
 && rm -rf /var/lib/apt/lists/*

RUN pip install prefect-redis

EXPOSE 4200

ENV PREFECT_API_HOST=0.0.0.0
ENV PREFECT_API_PORT=4200
