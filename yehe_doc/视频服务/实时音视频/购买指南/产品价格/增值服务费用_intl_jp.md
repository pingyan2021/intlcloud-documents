## 付加価値サービスの料金

付加価値サービスとは、インスタントメッセージング、クラウドレコーディング、クラウドミクスストリーミング、スクリーンキャプチャ、ポルノ検出等を指します。これらの機能は、IM、LVB、VOD等のその他のTencent Cloud製品と結合させて初めて実現できます。各項目の付加価値サービスにはいずれも独立した課金ルールがあり、関連費用は対応するTencent Cloud製品で清算されます。
**IMは、TRTCの無料試用版として提供され、他の付加価値サービスはデフォルトで無効になっています。付加価値サービスがアクティブ化された後、使用されない場合は課金されません**。


## IM料金

同じ製品内でTRTCとIMサービスを同時に統合しやすいように、TRTCアプリケーションを作成すると、システムがTRTCアプリケーションと同じSDK AppIDを持つIMアプリケーションを自動的に作成します。IMサービスではシングルチャット、グループチャット、メッセージプッシュ、データ・リレーションチェーンの管理、アカウント認証等のリアルタイム通信機能を提供することができます。

| 付加価値アイテム       | 課金製品                                                     | 課金の詳細                                                     |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| インスタントメッセージング | [IM](https://intl.cloud.tencent.com/document/product/1047) | IMの TRTC体験版は恒久的に無料です。実際のニーズに応じて様々なIMのバージョンをご購入いただけます。 |

>?TRTCアプリケーションとIMアプリケーションが同じSDKAppIDを持っている場合、それらは互いにアカウントと認証データを共有できます。

## Relayed live streaming料金

Relayed live streaming機能はデフォルトでオフ状態になっています。機能紹介と使用方法は、 [CDN Relayed Live Streaming](https://intl.cloud.tencent.com/document/product/647/34617)をご参照ください。

| 付加価値アイテム       | 課金製品   | 課金の詳細                                                     |
| :----------- | :--------- | :----------------------------------------------------------- |
| CDN Relayed Live Streaming | LVB | **トラフィック**または**帯域幅**にもとづき課金され、実際のニーズに応じてご自身に合った課金方式を選択することができます。デフォルトではトラフィック課金方式を採用します。 |

## クラウドレコーディング料金

クラウドレコーディング機能はデフォルトでオフになっています。機能紹介と使用方法は、 [クラウドレコーディング](https://intl.cloud.tencent.com/document/product/647/35152)をご参照ください。

| 付加価値アイテム                | 課金製品   | 課金の詳細                                                     |
| :------------------------- | :--------- | :----------------------------------------------------------- |
| LVBレコーディング                   | LVB | **当月のLVBレコーディングチャネルのピーク数**にもとづき課金されます。    |　　　
| ビデオファイル保存               | VOD | **VODプラットフォームに保存されているレコーディングファイルに使用されるストレージ容量**によって課金されます。 |　　　
| レコーディング済みのビデオファイルの再生またはダウンロード | VOD| **ダウンストリームのアクセラレーショントラフィック**によって課金されます。                   |　

>?クラウドレコーディング機能を利用してレコーディング費用が徴収された後に、トラフィック/帯域幅の費用が重複して徴収されることはありません。

## クラウドミクストランスコーディング料金

クラウドミクストランスコーディング機能はデフォルトでオフになっています。機能紹介と使用方法は [クラウドミクストランスコーディング](https://intl.cloud.tencent.com/document/product/647/34618)をご参照ください。この機能を利用するにはLVBサービスをアクティブ化し、さらにビジネスニーズに応じてLVBコンソールで トランスコーディング設定 を行う必要があります。

| 付加価値アイテム           | 課金製品                                                 | 課金の詳細                                                     |
| :--------------- | :------------------------------------------------------- | :----------------------------------------------------------- |
| クラウドミクストランスコーディング機能 | [LVB](https://intl.cloud.tencent.com/document/product/267) | **様々なコーディング方式と解像度に対応するクラウドミクストランスコーディングの時間**にもとづき課金されます。 |

## スクリーンキャプチャとポルノ検出料金

スクリーンキャプチャとポルノ情報の検出機能はデフォルトでオフになっています。機能紹介と使用方法は、 [スクリーンキャプチャとポルノ検出の設定](https://intl.cloud.tencent.com/document/product/267/31072)をご参照ください。

| 付加価値アイテム     | 課金製品                                                 | 課金の詳細                                  |
| :------- | :------------------------------------------------------- | :---------------------------------------- |
| LVBスクリーンキャプチャ | [LVB](https://intl.cloud.tencent.com/document/product/267) | **スクリーンキャプチャ数量**に応じて課金されます。    |
| インテリジェントなポルノ情報の検出 | [LVB](https://intl.cloud.tencent.com/document/product/267) | **ポルノ検出画像数**に応じて課金されます。 |
