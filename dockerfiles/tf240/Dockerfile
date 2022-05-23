# https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel_21-05.html#rel_21-05
# Ubuntu : 20.04
# CUDA   : 11.3.0
# cuDNN  : 8.2.0.51
# Python : 3.8
# Tensorflow : 2.4.0

FROM nvcr.io/nvidia/tensorflow:21.05-tf2-py3

# 環境変数
# ENV http_proxy 'http://id:pass@proxy:port' など

# コマンド実行
# RUN apt-get update && apt-get upgrade -y  など

# dockerfiles/requirements.txt をコピー
COPY ../requirements.txt .
RUN pip install -r requirements.txt