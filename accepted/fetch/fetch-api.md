# Fetch API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- アドオン内でセッション確立等のために外部との通信を行いたい。

## Requirements
- アドオンからGETリクエストを任意のURLに送信したい。
- アドオンからPUTリクエストを任意のURLに送信したい。
- 認証情報を含めた通信を行いたい。

### Goals
- アドオンからGETリクエストを任意のURLに送信できる。
- アドオンからPUTリクエストを任意のURLに送信できる。
- 認証情報を含めた通信を行うことができない。

### Non-Goals
- 上記の項目を達成できない

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### Permission
- ```session``` (if ```credentials``` is set to 'include')

### HostPermissions
- アクセス可能なホストの一覧。GoogleChrome拡張機能の[host_permissions](https://developer.chrome.com/docs/extensions/mv3/match_patterns/)をモデルにしています。
#### 設定例
```jsonc
//manifest.json
{
    ..
    "host_permissions": [
        "http://nicovideo.jp",
        "https://nicovideo.jp",
        "http://*.nicovideo.jp",
        "https://*.nicovideo.jp",
    ],
    ..
}
```

### API
``` TypeScript
//global
fetch(url:string,options:FetchOption):Promise<Response>;

interface Response {

    //リクエストの成功状態
    get ok(): boolean;

    //レスポンスを文字列として取得
    text(): Promise<string>;

}

interface FetchOption {
    //メソッド。デフォルトはGET
    method?: 'POST'|'GET', 

    /*
    認証情報を含める
    'include'を指定する場合、session権限が必要です。
    */
    credentials?: 'include'|'omit', 
    body?: string,
}
```

### Example
``` TypeScript
const url = "https://example.com";
let message:Response;
let content:string;

message = await fetch(url);
content = await message.text();

_output.write(content);

const data = {
    "firstName":"太郎",
    "lastName":"山田",
};

const options = {
    method: 'POST', 
    credentials: 'include', 
    body: JSON.stringify(data),
}

message = await fetch(url,options);

content = await message.text();
_output.write(content);
```

## Q & A

:question: Q. CORSには対応しないのですか？  
:heavy_check_mark: Niconicomeはアドオンのインストール時に、ユーザーに対してリクエストを送信できるドメインの許可を得る必要があるため、CORSの実装は必要ないと考えます。

## Revision
Date | Description
:---:| :---:
2021/08/21 | Fetch APIを定義。

## Applies to
Application | Target API Version
:--: | --
Niconicome | <= 1.1