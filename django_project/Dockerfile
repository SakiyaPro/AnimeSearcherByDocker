# 公式からpython3.7 on alpine linuxイメージをpull
FROM python:3.7-slim-buster

# 作業ディレクトリを設定
WORKDIR /usr/src/django_project

# 環境変数を設定
# Pythonがpyc filesとdiscへ書き込むことを防ぐ
ENV PYTHONDONTWRITEBYTECODE 1
# Pythonが標準入出力をバッファリングすることを防ぐ
ENV PYTHONUNBUFFERED 1

# Pipenvをインストール
RUN pip install --upgrade pip \
&& pip install pipenv

# ホストのpipfileをコンテナの作業ディレクトリにコピー
COPY ./Pipfile /usr/src/django_project/Pipfile

# pipfileからパッケージをインストールしてDjango環境を構築
RUN apt-get update \
&&apt-get -y install gcc libmariadb-dev
RUN pipenv install --skip-lock --system --dev

# ホストのカレントディレクトリ（現在はdjango_projectディレクトリ）を作業ディレクトリにコピー
COPY . /usr/src/django_project/