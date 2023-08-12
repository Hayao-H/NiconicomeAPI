# RemoteInfo

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- APIに変更があった場合、アプリケーション本体を更新せずに対応できれば、コンフリクト等の問題を避けられる。

## Requirements
- ```Hooks API```を利用することでアドオン開発者が動画情報取得を代替することができる。

### Goals
- アドオン開発者が動画情報取得を自由に行うことができる。

### Non-Goals
- ページ解析をアプリケーション本体が担う。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### API
```TypeScript
application.hooks.registerVideoInfoFunction(func: (videoID: string, trackID: string) => Promise<DmcInfo>): void;
```
**argments**
- DmcInfo: 動画ID。
- APIへのアクセスに必要なID。  

**returns**
- DmcInfo: 動画情報のインターフェース。詳細については、標準ライブラリの[当該ソース](https://github.com/Hayao-H/NiconicomeAddonCoreLib/blob/develop/%40types/net/hooks/types/dmcinfo.d.ts)を参照してください。


## Q & A
None

## Revision
Date | Description
:---:| :---:
2023/08/12 | APIを定義。

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.4.0