# https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel_20-01.html#rel_20-01
# Ubuntu : 18.04
# CUDA   : 10.2.89
# cuDNN  : 7.6.5
# Python : 3.6
# Tensorflow : 2.0.0

FROM nvcr.io/nvidia/tensorflow:20.01-tf2-py3

# 環境変数
# ENV http_proxy 'http://id:pass@proxy:port' など

# コマンド実行
# RUN apt-get update && apt-get upgrade -y  など

# dockerfiles/requirements.txt をコピー
COPY ../requirements.txt .
RUN pip install -r requirements.txt