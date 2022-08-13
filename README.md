# Ubuntu サーバー構築集

## 動作確認済み

- [WebARENA Indigo](https://web.arena.ne.jp/indigo/)
- Ubuntu 22.04、1 CPU、 1 GB

## ベースシステム準備

> ファイヤーウォールはIndigoで設定しておく
> - インバウンドルール
> - HTTP(80)、HTTPS(443)、SSH(22)
> - 0.0.0.0

- [WebARENA Indigo 向け](./01_Indigo.md)

## ベースサービス

- [Apache HTTP Server](./02_Apache.md)
  - SSL対応含む

## 開発ソフト

- [Node.js](./80_NodeJs.md)
- [OpenJDK](./80_OpenJDK.md)
  - Gradle含む

## データベース

- [MongoDB](./80_MongoDB.md)

## ソフトウェア

## ツール