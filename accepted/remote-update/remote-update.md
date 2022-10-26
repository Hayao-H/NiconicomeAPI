# Remote Update API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- アドオンが更新された際に、手動でサイトからダウンロードしてインストールし直すのは面倒なので、ダウンロード機能がほしい。また、ソフト側からダウンロード・インストールを一括で行いたい。

## Requirements
- アドオンの更新を確認。
- ソフトウェア側がファイルをダウンロードしてインストールすることができる。

### Goals
- 上記要件を満たす。

### Non-Goals
- 上記要件を満たさない。

## Stakeholders and Reviewers
- [Hayao-H](https://github.com/Hayao-H)

## Design

### Permission
```remoteUpdate```

#### リモート更新について
アドオンの[manifest.json](../manifest/manifest.md)に、以下の項目を定義してください。
- ```auto_update_policy.auto_update = true```
- ```auto_update_policy.updatejson-url = "<url/of/update.json>"``` 

> アドオンファイルはすべてのドメインからダウンロード可能ですが、公式アドオンはgithub.comでのみ配信する予定なので、同サイトのご利用をオススメします。

#### update.json
```jsonc
{
    "version" : "1.0.0", //アドオンのバージョン
    "application-file" : "https://github.com/hoge/fuga/releases/download/v1.0.0/my-addon-v1.0.0.zip", //アドオンのファイルURL（インストール可能なzipファイル）
    "changelog" : "https://github.com/hoge/fuga/releases/v1.0.0", //更新情報のURL（ユーザーにはリンクが表示されるだけです。）
}
```

#### その他
- update.jsonの文字コードはutf8を推奨します。それ以外の文字コードでの動作保証はいたしません。

## Q & A

## Revision
Date | Description
:---:| :---:
2022/04/03 | 初版作成
2022/04/09 | 実装予定バージョンを延期。
2022/10/14 | リモート更新機能に変更

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.3.0