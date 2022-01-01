# WebView API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- 別ウィンドウでコンテンツを表示し、ユーザーとの対話を図る。

## Requirements
- 別ウィンドウでコンテンツを表示したい。


### Goals
- 別ウィンドウでHTML + JS/CSSを表示できる。
- バックグラウンドから表示するコンテンツを制御できる。

### Non-Goals
- 別ウィンドウでHTML + JS/CSSを表示できない。
- バックグラウンドから表示するコンテンツを制御できない。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design


### Permission
```webview```

### API
```TypeScript

interface WindowHandle {

    /*
    タブを閉じます
    @returns 操作の成功状態を表す真偽値。
    */
    close(): Promise<boolean>;

    //引数で指定したhtmlを表示します。
    navigateToString(htmlContent: string): Promise<void>; 

    //WebView2側にメッセージを送信します。*1
    postMessage(message: string): void;

    //メッセージハンドラを追加します。
    addMessageHandler(handler: (message: string)=>void): void;

    //タブが既に閉じているかどうか
    get isClosed: boolean;

}

//Windowを追加します。
application.window.add(title: string): Promise<WindowHandle>;

```

### *1 About "Message"
- **WebView2側（受信）**

    [こちらのページ](https://docs.microsoft.com/ja-jp/dotnet/api/microsoft.web.webview2.core.corewebview2.postwebmessageasjson?view=webview2-dotnet-1.0.1054.31)（Microsoft公式、英語）の```Example```のコードの通りに実装してください。  

- **WebView2側（送信）**

    [こちらのページ](https://docs.microsoft.com/ja-jp/microsoft-edge/webview2/how-to/communicate-btwn-web-native)（Microsoft公式、日本語）の、「**postMessage を使用してメッセージ文字列を受信する**」の通りに実装してください。  

### About Resource
- ```resource```権限[(参照)](../resource/resource-api.md#permission)を取得すると、resourceディレクトリ内のコンテンツにURLでアクセスできます。
- resourceディレクトリは```https://nc-resource.nico/```にマップされます。
- 例えば、resource/my-special-script.jsというファイル配置になっている場合、htmlのheaderに```<script src="https://nc-resource.nico/my-special-script.js" />```と記載することで、スクリプトを通常のウェブサーバーから取得するように追加できます。

## Q & A

## Revision
Date | Description
:---:| :---:
2022/01/01 | 初版作成 

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= v1.2.0
