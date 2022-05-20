
## Docker × VSCode 環境で複数バージョンの TensorFlow（CUDA Toolkit）を使い分ける

#### 0. 実行した環境
- Windows 11 Pro
- Geforce Game Ready Driver : 512.15
- Docker Engine : 20.10.13

#### 1. Docker 環境の構築
[WSL2+Docker+VSCodeの開発環境構築とPythonでWebアプリを試すまで](https://zenn.dev/kcabo/articles/c4f9b7fecc503a) を参考に、Dockerfile からコンテナが作成できることを確認する。 また、使用するGPUに対応する GeForce Game Ready Driver（GPUドライバ）をインストールする。 ホストOSに CUDA Toolkit はインストールしない。

#### 2. Dockerfile のクローン
GitHub を開き、[docker-multi-tensorflow](https://github.com/chubachii/docker-multi-tensorflow)を Fork する。 VSCode から GitHub アカウントに接続し、  
`コマンドパレット -> Git: Clone -> Clone from GitHub`  
で Fork したリポジトリを選択する。

#### 3. docker-compose.yml の編集
docker-compseは複数のコンテナを一つのまとまりとして管理できる。  サービス（コンテナ）名は TensorFlow のバージョンを取り、tf260（ TensorFlow 2.6.0 ）のように名づけている。  
まず、使用したい TensorFlow のバージョンに対応する dockerfile が `docker-multi-tensorflow -> dockerfiles` に存在するかを確認する。 ない場合は [dockerfile の作成方法](#dockerfile-の作成方法)を参考に追加する。  
次に docker-compose.yml を開き TensorFlow 2.6.0 の例を参考に、使用したいバージョンのサービスを追加する。

#### 4. コンテナの起動
VSCode 左下の >< から、`Open Folder in Container... -> dockerfiles -> tf xxx（使用したいバージョン）`自動的にコンテナが起動する。 初回起動時は 2.5GB 程度の image を pull する。 コンテナ起動後、
``` bash
python3 version.py
```
で TensorFlow のバージョンを確認できる。

#### dockerfile の作成方法
dockerfiles 内の適当なフォルダー（ tf260 など）を複製し、`.devcontainer/devcontainer.json`内、name、service の値を修正する。 [NVIDIA Docker のリリースノート](https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/)を開き、使用したいバージョンの TensorFlow が含まれている Container Version を探し出す（ページ下部に対応表あり）。 ページの説明を参考に dockerfile 内、
``` dockerfile
FROM nvcr.io/nvidia/tensorflow:21.10-tf2-py3
```
の tag（ 20.01-tf2-py3 ）を書き換える。

#### コンテナ生成時のエラーの対処法
[コンテナの起動](#4-コンテナの起動)でエラーが出る場合、ターミナルから事前に
`docker image pull nvcr.io/nvidia/tensorflow:21.10-tf2-py3`（Dockerfile 内 FROM 先を参考に変更する）
実行することで対処できる可能性がある。 もしくは再起動。