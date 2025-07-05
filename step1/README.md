# step1

`--privileged`フラグを利用したコンテナ脱出

Seccomp、AppArmor、SELinuxなどのセキュリティ機能を無効化するフラグ。

## `--privileged` のユースケース

- Docker in Docker(DinD)
- ハードウェアデバイスへのアクセス
- ホストのカーネルパラメーターの変更
