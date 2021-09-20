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

    downloadVideo: bool;

    downloadComment: bool;

    downloadLog: bool;

    downloadOwner: bool;

    downloadEasy: bool;

    downloadThumbnail: bool;

    downloadDescription: bool;

    downloadIchiba: bool;

    limitComment: bool;

    commentLimitCount: number;

    videoResolution: 1080 | 720 | 480 | 360 | 240;

    thumbnailSize: 'player' | 'large' | 'normal' | 'medium' | 'normal';

    overwriteIfExist: bool;

    skipIfExist: bool;

    copyIfExist: bool;

    disableEncode: bool;

    startDownload(): Promise;

    cancelDownload(): Promise;

    stageSelectedVideos(): Promise;

}
```

## Q & A
None

## Revision
Date | Description
:---:| :---:
2021/09/20 | 初版作成

## Applies to
Application | Target API Version
:--: | --
Niconicome | >=1.2.0