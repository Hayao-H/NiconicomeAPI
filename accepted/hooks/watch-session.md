# Watch Session

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- Dアニメ等の特殊な動画の場合、ユーザーがある程度アプリケーションのDL操作に介入できるようにしたい。

## Requirements
- ```Hooks API```で取得したJavaScriptオブジェクトを受け取ることで、ユーザーが自由にセッション確立操作を行うことができるようにする。

### Goals
- ユーザーがセッションの構築を自由に行うことができる。

### Non-Goals
- セッションの構築をアプリケーション本体が担う。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

#### API
```TypeScript
application.hooks.registerSessionEnsuringFunction(func: (info: DmcInfo) => SessionInfo): void;

interface SessionInfo {

    //HeartBeatで送信するコンテンツ
    DmcResponseJsonData:string;

    //プレイリストのURL
    ContentUrl:string;

    //セッションID
    SessionId:string;
}
```

## Q & A
None

## Revision
Target API Version | Date | Description
--- | :---:| :---:
v1.1.0 | 2021/08/21 | Watch Sessionの定義を追加。