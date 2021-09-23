# Download Settings API

**Owner** [Hayao-H](https://github.com/Hayao-H)

## Scenarios and User Experience
- ダウンロード設定画面を代替する拡張機能を作りたい。

## Requirements
- 拡張機能側からダウンロード設定を変更したい。
- 拡張機能側からダウンロードを開始したい。

### Goals
- 拡張機能側からダウンロード設定を変更できる。
- 拡張機能側からダウンロードを開始できる。

### Non-Goals
- 拡張機能側からダウンロード設定を変更できない。
- 拡張機能側からダウンロードを開始でない。

## Stakeholders and Reviewers
- (Owner)[Hayao-H](https://github.com/Hayao-H)

## Design

### Permission
```downloadSettings```

### API

```TypeScript
application.downloadSettings: DownloadSettings;

interface DownloadSettings {

    //ダウンロードの可否を表します。
    get canDownload: bool;

    //動画DLフラグ
    downloadVideo: bool;

    //コメントDLフラグ
    downloadComment: bool;

    //過去ログDLフラグ
    downloadLog: bool;

    //投稿者コメントDLフラグ
    downloadOwner: bool;

    //かんたんコメントDLフラグ
    downloadEasy: bool;

    //サムネイルDLフラグ
    downloadThumbnail: bool;

    //動画情報DLフラグ
    downloadDescription: bool;

    //市場情報DLフラグ
    downloadIchiba: bool;

    //コメント数制限フラグ
    limitComment: bool;

    //最大取得コメント数（コメント数制限が有効な場合のみ）
    commentLimitCount: number;

    //解像度
    videoResolution: 1080 | 720 | 480 | 360 | 240;

    //サムネイルの解像度
    thumbnailSize: 'player' | 'large' | 'normal' | 'medium' | 'normal';

    //動画が存在する場合上書き
    overwriteIfExist: bool;

    //動画が存在する場合スキップ
    skipIfExist: bool;

    //他フォルダーに動画が存在する場合コピー
    copyIfExist: bool;

    //MP4への変換すをスキップ
    disableEncode: bool;

    //DLを開始する
    startDownload(): Promise<void>;

    //DLをキャンセルする
    cancelDownload(): void;

    //選択した動画をステージする
    stageSelectedVideos(): Promise;

}
```

## Q & A
None

## Revision
Date | Description
:---:| :---:
2021/09/20 | 初版作成
2021/09/21 | 説明を追加。一部の非同期APIを同期化。

## Applies to
Application | Target API Version
:--: | --
Niconicome | >= 1.2.0