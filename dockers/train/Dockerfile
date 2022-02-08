FROM python:3.9
MAINTAINER wenliangz@gmail.com

COPY ./dockers/train/requirements.txt /app/
COPY ./scripts/ /app/scripts/
COPY ./data/ /app/data/
WORKDIR /app
RUN pip install -r requirements.txt
#CMD ["uvicorn", "scripts.api_main:app", "--reload"]