# https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel_21-10.html#rel_21-10
# Ubuntu : 20.04
# CUDA   : 11.4.2
# cuDNN  : 8.2.4.15
# Python : 3.8
# Tensorflow : 2.6.0

FROM nvcr.io/nvidia/tensorflow:21.10-tf2-py3

# 環境変数
# ENV http_proxy 'http://id:pass@proxy:port' など

# コマンド実行
# RUN apt-get update && apt-get upgrade -y など

# dockerfiles/requirements.txt をコピー
COPY ../requirements.txt .
RUN pip install -r requirements.txt