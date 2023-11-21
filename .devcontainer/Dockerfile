# DockerHubのベースとなるイメージを指定
FROM python:3.10.12-slim

# 作業ディレクトリを変更
WORKDIR /python_econometrics

# ローカルPCのファイルをコンテナのカレントディレクトリにコピー
COPY requirements.txt ${pwd}

RUN apt update && apt -y upgrade && apt install -y vim gcc libgraphviz-dev

# pipのアップデート
RUN pip install --upgrade pip

# pythonパッケージをインストール
RUN pip install -r requirements.txt

# コンテナ起動時に実行するコマンドを指定
CMD ["/bin/bash"]

