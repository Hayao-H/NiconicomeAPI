# Search

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- 検索システムに変更があった場合、アプリケーション本体を更新せずに対応できれば、コンフリクト等の問題を避けられる。

## Requirements
- ```Hooks API```を利用することでアドオン開発者が検索機能を代替することができる。

### Goals
- アドオン開発者が開発者が検索を自由に行うことができる。

### Non-Goals
- 検索をアプリケーション本体が担う。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### API
```TypeScript
application.hooks.registerSearchFunction(func: (param: string,page:number,  type: "tag" | "keyWord", orderBy: "viewCount"|"postAt"|"commentCount"|"mylistCount"|"duration",order:"ascending"|"descending") : SearchResult): void;
```
**argments**
- param：検索キーワード
- type：検索方式
- orderBy：並び替えの基準

    文字列 | 内容
    --- | ---
    viewCount | 視聴回数
    postAt | 投稿日時
    commentCount | コメント数
    mylistCount | マイリスト数
    duration | 動画の長さ

- order：昇順・降順


**returns**
- SearchResult: 検索結果のインターフェース。詳細については、標準ライブラリの[当該ソース](https://github.com/Hayao-H/NiconicomeAddonCoreLib/blob/develop/%40types/net/hooks/types/searchResult.d.ts)を参照してください。


## Q & A
None

## Revision
Date | Description
:---:| :---:
2024/09/13 | API定義

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.5.0