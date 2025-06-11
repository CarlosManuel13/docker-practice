FROM python:3.13

# FROM ubuntu:22.04

# RUN apt-get update && apt-get install -y python3 python3-venv

WORKDIR /app
RUN python3 -m venv .venv

ENV VIRTUAL_ENV=/app/.venv
ENV PATH="${VIRTUAL_ENV}/bin:$PATH"
ENV FLASK_APP=src.app

COPY requirements.txt .

RUN python3 -m pip install -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["flask","run","--host","0.0.0.0"]
