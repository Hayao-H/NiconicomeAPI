# Hooks API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- ニコニコ側の変更に柔軟に対応できるようにする。

## Requirements
- ユーザーがアプリケーションのDL動作に介入できるようにすることで、変更に強いアプリケーションを構築する。

### Goals
- ユーザーが自由にDL関連の挙動を操作できる。

### Non-Goals
- サーバーの変更でアプリケーション自体の更新が必要になる。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### Permission
```hooks```

### API
```TypeScript
//関数の登録状況を確認
application.hooks.isRegistered(hookType: "PageAnalyze" | "WatchSession" | "RemoteInfo");
```

### Detailed Infomations
- [PageAnalyze](./page-analyze.md)
- [WatchSession](./watch-session.md)
- [RemoteInfo](./remote-info.md)

### Permission
```hooks```

## Q & A
None

## Revision
Date | Description
:---:| :---:
2021/08/17 | APIを定義。
2021/08/21 | Watch Sessionへのリンクを追加。
2021/09/20 | APIバージョンの表記を修正
2023/08/15 | 関数の登録状況確認APIを追加。

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.4.0