FROM python:3.9
MAINTAINER wenliangz@gmail.com

COPY ./dockers/predict/requirements.txt /app/
COPY ./scripts/ /app/scripts/
COPY ./model/ /app/model/
WORKDIR /app
RUN pip install -r requirements.txt
#CMD ["uvicorn", "scripts.api_main:app", "--reload"]