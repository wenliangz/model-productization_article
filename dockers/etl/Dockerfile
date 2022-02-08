FROM python:3.9
MAINTAINER wenliangz@gmail.com

COPY ./dockers/etl/requirements.txt /app/
COPY ./scripts/ /app/scripts/
COPY ./data/ /app/data/
WORKDIR /app
RUN pip install -r requirements.txt