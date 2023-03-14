FROM jupyter/scipy-notebook

#USER root заходим под root если корневая папка под root меняем на jovyan:users 
USER jovyan

WORKDIR /home/jovyan/app 

RUN pip install --upgrade SQLAlchemy==1.4.46

EXPOSE 5000 

RUN conda install --quiet --yes \
    'mlflow==1.26.1' \
    'scikit-learn==1.1.1' \
    'psycopg2-binary'

# RUN conda install --quiet --yes \
#     'mlflow==1.26.1' \
#     'scikit-learn==1.1.1' \
#     'psycopg2'