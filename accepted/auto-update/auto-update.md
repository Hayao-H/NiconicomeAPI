# Auto Update API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- アドオンが更新された際に、手動でインストールし直すのは面倒なので、自動更新機能がほしい。

## Requirements
- アドオンが更新されたことを検知してバックグラウンドで自動更新。
- アドオンに権限が追加された際は、ユーザーに承認を求める。
- 自動更新の有効・無効を切替可能。

### Goals
- 上記要件を満たす。

### Non-Goals
- 上記要件を満たさない。

## Stakeholders and Reviewers
- [Hayao-H](https://github.com/Hayao-H)

## Design

#### 自動更新について
アドオンの[manifest.json](../manifest/manifest.md)に、以下の項目を定義してください。
- ```auto_update_policy.auto_update = true```
- ```auto_update_policy.updatejson-url = "<url/of/update.json>"``` 

> アドオンファイルはすべてのドメインからダウンロード可能ですが、公式アドオンはgithub.comでのみ配信する予定なので、同サイトのご利用をオススメします。

#### update.json
```json
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

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.2.0