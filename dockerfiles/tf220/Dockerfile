# https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel_20-08.html#rel_20-08
# Ubuntu : 18.04
# CUDA   : 11.0.3
# cuDNN  : 8.0.2
# Python : 3.6
# Tensorflow : 2.2.0

FROM nvcr.io/nvidia/tensorflow:20.08-tf2-py3

# 環境変数
# ENV http_proxy 'http://id:pass@proxy:port' など

# コマンド実行
# RUN apt-get update && apt-get upgrade -y  など

# dockerfiles/requirements.txt をコピー
COPY ../requirements.txt .
RUN pip install -r requirements.txt