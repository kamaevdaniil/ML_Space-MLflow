# Mlfow example: Tracking, Model, Model Registry, Serving

***


**MLflow** — это платформа для оптимизации разработки машинного обучения, которая включает:

- отслеживание экспериментовниже;
- упаковка кода для совместного использования;
- инструменты упаковки модели;
- централизованное хранилище моделей.

Далее привидены примеры использования Mlflow, как на локальном хосте так и с использованием технологии Docker

### Установка

Установите MLflow из PyPI через `pip install mlflow`
Перед эти необходимо установить `conda` 

### Документация

Официальная документация: https://mlflow.org/docs/latest/index.html

## Mlflow Tracking





### `Example 1`: MLflow on localhost

Для запуска MlflowClient на localhost c файловым хранилищем:` mlflow ui -p 5000 --host 0.0.0.0 `

Автамотически в корне проекта создаётся папка `./mlruns` в которую сохраняються прогоны и артефакты 

**Пример для запуска**: `/myapp/sample_1_local.ipynb`

> *Удалённые эксперементы храняться в папке **./mlruns/.trash***

![Local_ex_1!](src/images/example_1_local.png "Local_ex_1")






### `Example 2`: MLflow on localhost with SQLite

Для запуска **MlflowClient** на **localhost c sqlite хранилищем**:

`mlflow ui -p 5000 --host 0.0.0.0  --backend-store-uri sqlite:///mlruns.db`

**Пример для запуска**: `/myapp/sample_2_local_sqlite.ipynb`

**Важно** в коде указывать mlflow.set_tracking_uri('http://localhost:5000') так как прогоны отслеживаются отслеживаются

> **Mlflow Client** создаёт файл **mlruns.db** в который записывает прогоны
> **Mlflow Models** работает только с sqlite хранилищем см.документацию

![Local_ex_2!](src/images/example_2_local_sqlite.PNG "Local_ex_2")






### `Example 3`: MLflow on Docker with TrackingServer 

#### `Docker compose`:  Mlflow remote server with Sqlite + jupyter/noteebok (Mlflow client) 

В данном примере понадобиться:

- docker compose ,c двумя сервисами:
    - Первый сервис: образ **[jupyter/scipy-notebook](https://hub.docker.com/r/jupyter/scipy-notebook)**

    - Второй сервис: образ **[python:3.9.13-slim](https://hub.docker.com/r/jupyter/scipy-notebook)**

- #### для развёртывания примера собрать и поднять контейнеры следующей коммандой: `docker compose --env-file notebook_remote.env up --build`

    - файл  `notebook_remote.env` с переменными среды для сборки

- #### Пример `myapp/sample3_remote_server.ipynb`

- Команда для запуска удалённого сервера **Mlflow**
  в качестве **бд** `sqlite`, для записи прогонов,
  в качестве хранилища артефактов **URI** до папки `/mlruns `
> **CMD mlflow server \
    --backend-store-uri sqlite:///mydb.sqlite \\
    --default-artifact-root file:///home/jovyan/app/mlruns \\
    --host 0.0.0.0**







![Local_ex_3!](src/images/example_3_tracking_sqlite.PNG "Local_ex_3")



### `Example 4`: MLflow with remote Tracking Server, backend and artifact stores

#### `Docker compose`:  Mlflow remote server + jupyter/noteebok with Mlflow client + file-store postgres + artifact-store ftp-server


<
![Local_ex_4!](src/images/example_4.png "Local_ex_4")







