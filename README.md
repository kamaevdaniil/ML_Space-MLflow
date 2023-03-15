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
mlflow ui -p 5000 --host 0.0.0.0  --backend-store-uri sqlite:///mlruns.db

**Пример для запуска**: `/myapp/sample_2_local_sqlite.ipynb`

![Local_ex_2!](src/images/example_2_local_sqlite.PNG "Local_ex_2")






### `Example 3`: MLflow on localhost with TrackingServer 

#### `Docker compose`:  Mlflow remote server + jupyter/noteebok with Mlflow client and sqlite file-store




![Local_ex_3!](src/images/example_3_tracking_sqlite.PNG "Local_ex_3")



### `Example 4`: MLflow with remote Tracking Server, backend and artifact stores

#### `Docker compose`:  Mlflow remote server + jupyter/noteebok with Mlflow client + file-store postgres + artifact-store ftp-server


<
![Local_ex_4!](src/images/example_4.png "Local_ex_4")







