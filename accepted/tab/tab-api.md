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

    //タブを閉じます
    close(): Promise<bool>;

    //引数で指定したhtmlを表示します。
    navigateToString(htmlContent: string): Promise<void>; 

    //タブが閉じれれているかどうか
    get isClosed: bool;

}

//タブを追加します。
application.tab.add(): TabHandle;

/*
デフォルトタブを隠します。
現在は「設定」タブのみです。
*/
application.tab.hideDefaultTab(tabName: 'downloadSetting');

```

## Q & A

## Revision
Date | Description
:---:| :---:
2021/09/21 | 初版作成

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= v1.2.0