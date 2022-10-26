# Manifest

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- アドオンをアプリケーションに読み込ませるための情報を容易に定義できる仕組みがほしい。

## Requirements
- アドオンをアプリケーションに読み込ませるための情報を容易に定義できるようにする。

### Goals
- アドオン開発者がアドオン定義を容易に行うことができる。

### Non-Goals
- アドオン開発者がアドオン定義を行うことができない、または複雑である。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### General
- ブラウザーのアドオンなどに合わせて、マニフェストファイルと呼称し、Jsonで定義できるようにすることでより読みやすいインターフェースを構築する。

### File Name (Perfect matching)
```manfest.json```

### Types

#### 注釈について
- ```【必須】```：必ず定義。
- ```【推奨】```：定義をお勧めします。
- ```【任意】```：必要に応じて定義してください。 
```jsonc
    {
        "manifest_version": "1.1", //マニフェストバージョン【必須】 *1
        "scripts": {
            /*
            バックグラウンドスクリプトです。【必須】
            アドオンが読み込まれると自動的に実行されます。
            */
            "background_script": "scripts/main.js" ,
        },
        "name": "", //アドオン名【必須】
        "author": "", //作者名【必須】
        "description": "", //説明【必須】
        "homepage": "", //ホームページ【推奨】
        /*
        バージョン。【必須】
        同一バージョンは上書きインストールできません。
        */
        "version": "1.2.0", 
        /*
        同時インストール防止のユニークキー【推奨】
        */
        "identifier": "page-analyze-plugin", 
        /*
        ターゲットAPIバージョン。【必須】
        APIの互換性のないバージョンへのインストールを防ぐことができます。
        */
        "target_api_version": "1.0.1",　
        /*
        権限。【任意】*2
        必要な場合に定義してください。
        */
        "permissions": [
            "hooks",
            "output",
            "log"
        ],
        /*
        ホスト権限【任意】*3
        Fetch APIを利用する場合に定義してください。
        */
        "host_permissions": [],
        /*
        アイコン。【必須】
        32pxが定義されている場合、そちらを優先して読み込みます。
        */
        "icons": {
            "32": "icons/32.png",
            "128": "icons/128.png"
        },
        /*
        リモートアップデート関連の設定。（ターゲットAPIバージョン1.3.0以上で利用可能です。*4）【任意】
        */
        "remote_update_policy": { 
            "updatejson-url": "https://raw.githubusercontent.com/Hayao-H/PageAnalyzePlugin/update/update.json", //update.jsonのURL（MIMEタイプはapplication/jsonでなくとも問題ありません。）
        },
    }
```

#### *1 マニフェストバージョン
現行のマニフェストバージョンは**1.1**です。  
このバージョンはマニフェストファイルに破壊的変更が行われた際に変更されます。  
項目の追加は破壊的変更に当たらないので変更されません。

#### *2 権限の一覧
- hooks ([参照](../hooks/hooks-api.md))
- output ([参照](../output/output-api.md))
- log ([参照](../log/log-api.md))
- session([参照](../fetch/fetch-api.md#Permission));
- resource([参照](../resource/resource-api.md#Permission))
- storage([参照](../storage/storage-api.md#Permission))
- tab([参照](../tab/tab-api.md#Permission))
- downloadSettings([参照](../download-settings/download-settings-api.md#permission))
- remoteUpdate([参照](../remote-update/remote-update.md#permission))

### *3 ホスト権限
パターンマッチングを利用できます。  
詳しくは[こちら](../fetch/fetch-api.md#HostPermissions)
#### 例
```
[
    "https://*.nicovideo.jp",
    "http://*.nicovideo.jp"
]
```

### *4 自動アップデート
アップデート情報ファイルをホストすることでアドオンを自動的にアップデートさせることができます。
詳しくは[こちら](../remote-update/remote-update.md)


## Q & A
None

## Revision
Date | Description
:---:| :---:
2021/08/17 | 初版作成。
2021/08/21 | Fetch APIに関するリンクを追加。
2021/09/20 | APIバージョンの表記を修正
2021/09/23 | 権限を追加
2022/01/01 | ホスト権限の例を修正。
2022/03/29 | 権限を追加。
2022/04/03 | 自動更新についての記述を追加。
2022/04/09 | 自動更新機能の実装を延期。
2022/10/14 | リモート更新に変更。
2022/10/25 | マニフェストのバージョンを変更。ホームページ情報を追加。

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.0