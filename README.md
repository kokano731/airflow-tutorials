# airflow-tutorials

## 概要

Airflowの実行環境を構築して、Tutorialsを試してみる。

Tutorials:  
https://airflow.apache.org/docs/apache-airflow/stable/tutorial/index.html

実行環境は、簡単にできるようGCPのCloud Shell上にpipを用いて構築する。  
構築手順は以下のQuick Startの手順を参照。

Quick Start:  
https://airflow.apache.org/docs/apache-airflow/stable/start.html

## 実行環境

Google Cloudコンソールを開き、"Cloud Shellをアクティブにする"アイコンをクリック。

Cloud Shellで以降のコマンドを実行してAirflowをインストール。

venvで作成した仮想環境にインストールする。

```
$ python -m venv airflow-env
$ source  airflow-env/bin/activate
```

Airflowのインストール。

```
$ mkdir -p airflow (ホームディレクトリ、適宜変更)
$ export AIRFLOW_HOME=~/airflow
$ AIRFLOW_VERSION=2.6.0
$ PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
$ CONSTRAINT_URL=https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt
$ pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
```

Airflowを起動。
Cloudコンソールの"ウエブでプレビュー"アイコンをクリックして、
ブラウザからAirflow UI画面にアクセス。  
(http://localhost:8080/にアクセス)

「ログイン画面」

Usernameは`admin`、Passwordは起動時のログ中に表示されていたもの、
```
standalone | 
standalone | Airflow is ready
standalone | Login with username: admin  password: *********
standalone | Airflow Standalone is for development purposes only. Do not use this in production!
standalone |
```
もしくは、`$AIRFLOW_HOME/standalone_admin_password.txt`
に記載されているものを入力。

「DAGs画面」
