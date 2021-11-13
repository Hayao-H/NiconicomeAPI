# Tab API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- 新たなタブを追加して、ユーザーとの対話を図る。

## Requirements
-  新たなタブを追加したい。

### Goals
- 新たなタブを追加できる。
- タブで表示するコンテンツを操作できる。
- 許可したホストのみ表示できる。
- タブを閉じることができる。

### Non-Goals
- 新たなタブを追加できない。
- タブで表示するコンテンツを操作できない。
- 許可しないホストでも表示できる。
- タブを閉じることができない。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### Permission
```tab```

### API
```TypeScript

interface TabHandle {

    /*
    タブを閉じます
    @returns 操作の成功状態を表す真偽値。
    */
    close(): Promise<boolean>;

    //引数で指定したhtmlを表示します。
    navigateToString(htmlContent: string): Promise<void>; 

    //タブが既に閉じているかどうか
    get isClosed: boolean;

}

//タブを追加します。
application.tab.add(title: string): Promise<TabHandle>;

```

### About Resource
- ```resource```権限[(参照)](../resource/resource-api.md#permission)を取得すると、resourceディレクトリ内のコンテンツにURLでアクセスできます。
- resourceディレクトリは```https://nc-resource.nico/```にマップされます。
- 例えば、resource/my-special-script.jsというファイル配置になっている場合、htmlのheaderに```<script src="https://nc-resource.nico/my-special-script.js" />```と記載することで、スクリプトを通常のウェブサーバーから取得するように追加できます。


## Q & A

## Revision
Date | Description
:---:| :---:
2021/09/21 | 初版作成
2021/09/23 | リソースに関する定義を追加。
2021/11/13 | 規定タブ削除APIを一旦削除。引数の訂正。APIを非同期化。

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= v1.2.0