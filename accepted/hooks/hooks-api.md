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

### Detailed Infomations
- [PageAnalyze](./page-analyze.md)
- [WatchSession](./watch-session.md)

### Permission
```hooks```

## Q & A
None

## Revision
Target API Version | Date | Description
--- | :---:| :---:
v1.0 | - | -
v1.1.0 | 2021/08/21 | Watch Sessionへのリンクを追加。