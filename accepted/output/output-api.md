# Output API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- アドオン開発者が、ユーザーに対して何らかの通知を行う場合の手段を提供する。

## Requirements
- ```出力```タブに文字列を書き込む。

### Goals
- ```出力```タブに文字列を書き込む事ができる。

### Non-Goals
- アドオン開発者がユーザーに対する通知手段を持たない

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)


## Design

### Permission
```output```

### API
```TypeScript
application.output.write(message: unknown): void;
application.output.write(message: string): void;
```
***argments***
- message: 出力する文字列。
## Q & A

## Revision
Date | Description
:---:| :---:
2021/08/17 | Log APIの定義を追加。
2021/09/20 | APIバージョンの表記を修正

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.0