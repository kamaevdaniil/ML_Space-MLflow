FROM python:3.9.13-slim

ARG UNAME
ARG UID
ARG GID
# USER jovyan

WORKDIR /app

RUN pip install --upgrade pip && \
    pip install --no-cache-dir 'mlflow==1.26.1'

#Строчка ниже для работы бд иначе будет ошибка 
RUN pip install --upgrade SQLAlchemy==1.4.46
RUN pip install psycopg2-binary

RUN mkdir /mlflow/

EXPOSE 5000

# UID and GID храниться в etc/passwd смотреть в сервисе с кодом

RUN groupadd -g $GID -o $UNAME
RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME

USER root

CMD mlflow server \
    --backend-store-uri postgresql://admin:secret@postgres:5432/mlflow \
    --default-artifact-root ftp://mlflow:mlflow_password@localhost/data \ 
    --host 0.0.0.0 






