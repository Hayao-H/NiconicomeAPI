# Storage API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
アドオン内でデータを永続化したい。

## Requirements
- 文字列データを永続化できる。
- 登録したデータを削除できる。
- 登録したデータを取得できる。

### Goals
データの永続化を行うことができる。

### Non-Goals
データの永続化を行うことができない。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)


## Design

### Permission 
``storage``

### Detailed Infomation
- [LocalStorage](./localStorage.md)

## Q & A

## Revision
Date | Description
:---:| :---:
2021/08/27 | 初版作成。
2021/09/20 | APIバージョンの表記を修正

## Applies to
Application | Target API Version
:--: | --
Niconicome | >=v1.2.0