# Attention!
__検索避けの為、Starはつけないでください!!!!__

# 環境構築手順
勤怠管理システム（管理画面）を例に環境構築の補足事項をまとめます。

## 前提事項
- [環境用リポジトリ](https://github.com/Innovative-Lab/attend-pro-environment) がcloneされていること
- 基本的にReadMeに記載されているコマンドはそのリポジトリの階層で叩きます。

## 1. 初回設定を行う
1. [初回設定](https://github.com/Innovative-Lab/attend-pro-environment?tab=readme-ov-file#%E5%88%9D%E5%9B%9E%E8%A8%AD%E5%AE%9A)の1-3を実行する。
2. cloneした `attend-pro-environment`配下で `./setup.sh` を実行する。
    1. 途中で `YES` or `No` を聞かれるので `YES` を入力してEnterを押下します。
    2. 具体的にこのシェルで何が行われているかは実際に [setup.sh](https://github.com/Innovative-Lab/attend-pro-environment/blob/main/setup.sh)を参照。
    3. 各種変数定義や、miseのインストール、etc..を行なっています。
4. セットアップ完了メッセージ表示後、メッセージに沿って シェルの再起動コマンドを叩きます。
    1. 再起動コマンド：`exec $SHELL -l`
## 2.管理画面起動準備
1. Readmeに沿って [Docker](https://github.com/Innovative-Lab/attend-pro-environment/tree/main?tab=readme-ov-file#docker)の起動コマンドを実行。
2. Readmeに沿って [envファイル作成](https://github.com/Innovative-Lab/attend-pro-admin/tree/main?tab=readme-ov-file#env%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E4%BD%9C%E6%88%90)を行う。
3. `attend-pro-environment/attend-pro-admin/scripts` 配下で `./all_update.sh` を実行する。
    1. 具体的にこのシェルで何が行われているかは実際に [all_update.sh](https://github.com/Innovative-Lab/attend-pro-admin/blob/main/scripts/all_update.sh)を参照。
    2. 依存環境のインストール、生成、DBマイグレーション、シードデータの投入を行なっています。
4. `attend-pro-environment/attend-pro-admin/`配下で [起動コマンド](https://github.com/Innovative-Lab/attend-pro-admin/tree/main?tab=readme-ov-file#%E8%B5%B7%E5%8B%95)を実行。
5. ReadMeに記載されている、URLをブラウザで開くとログイン画面が表示される。
6. メールアドレスとパスワードにてログイン出来れば管理画面の環境構築は完了。
## 困った時
1. `mise python@3.11.0 patching file 'test/v3ext.c’` で動かなくなった場合
    1. 下記コマンドでXCodeをインストールし、再度`./setup.sh` を実行する。
```
$ xcode-select --install
```
2. `mise WARN  missing: python@3.10.0` が出た場合
    1. [.mise.toml](https://github.com/Innovative-Lab/attend-pro-environment/blob/main/.mise.toml#L44)のpythonのバージョンを3.11に変更し、再度`./setup.sh` を実行する。
