# https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel_20-12.html#rel_20-12
# Ubuntu : 20.04
# CUDA   : 11.1.1
# cuDNN  : 8.0.5
# Python : 3.8
# Tensorflow : 2.3.1

FROM nvcr.io/nvidia/tensorflow:20.12-tf2-py3

# 環境変数
# ENV http_proxy 'http://id:pass@proxy:port' など

# コマンド実行
# RUN apt-get update && apt-get upgrade -y  など

# dockerfiles/requirements.txt をコピー
COPY ../requirements.txt .
RUN pip install -r requirements.txt