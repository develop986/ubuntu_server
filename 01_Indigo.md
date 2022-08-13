# Ubuntu 22.04.1 LTS

## SSHで外部接続出来るようにする
```
& mkdir .ssh
& cp ~/ダウンロード/private_key.txt /home/kuhataku/.ssh/authorized_keys
$ chmod 600 .ssh/authorized_keys
$ rm .ssh/known_hosts*
$ ssh -i ~/.ssh/authorized_keys ubuntu@mysv986.com
$ sudo su -
```

## アップデート
```
# apt update && apt -y full-upgrade
# reboot
```

## 設定情報の履歴を取れるようにする
```
# apt install -y etckeeper
# etckeeper init
# etckeeper commit "1st commit"
```

## デフォルトエディタ変更

```
$ update-alternatives --config editor
# update-alternatives --set editor /usr/bin/vim.basic
```

## 日本設定
```
# timedatectl set-timezone Asia/Tokyo
# timedatectl status
# apt install -y language-pack-ja
# localectl set-locale LANG=ja_JP.UTF-8
# localectl list-locales
# reboot
# date

以下のように表示される
2022年  8月 13日 土曜日 10:47:16 JST
```

## ホスト名変更
```
# hostnamectl set-hostname mysv986.com
```

## 自動アップデート設定
```
# vi /etc/apt/apt.conf.d/50unattended-upgrades

//Unattended-Upgrade::Automatic-Reboot "false";
Unattended-Upgrade::Automatic-Reboot "true";
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";
Unattended-Upgrade::Automatic-Reboot-Time "05:00";

但し、その時間で再起動されるのは未検証

# reboot
```

## SWAP設定
```
# free -m
# dd if=/dev/zero of=/swapfile bs=1M count=1024
# chmod 600 /swapfile
# mkswap /swapfile
# swapon /swapfile
# sed -i '$ a /swapfile                                 swap                    swap    defaults        0 0' /etc/fstab
# free -m
# reboot
# free -m
``` 

## ファイアウォール構築
```
```

## 接続用アカウント作成
```
# userdel -r remoteadmin
# useradd remoteadmin
# passwd remoteadmin
# visudo
remoteadmin	ALL=(ALL)	NOPASSWD: ALL

# reboot
```

## Cockpit インストール（Web管理コンソール）

> 適切なファイヤーウォール設定をして下さい

```
# apt -y install cockpit
# systemctl enable cockpit.socket

https://mysv986.com:9090
```