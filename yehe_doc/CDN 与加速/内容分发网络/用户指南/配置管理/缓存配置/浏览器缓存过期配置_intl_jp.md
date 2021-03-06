## 機能の概要

ブラウザのキャッシュ有効期限を設定することで、クライアントのブラウザのキャッシュポリシーをカスタマイズして、back-to-origin率を下げることができます。

> ?リソースをリクエストするとき、リクエストされたリソースがブラウザにキャッシュされている場合は直接返されます。ブラウザにキャッシュされていない場合は、リクエストはCDNキャッシュノードに転送されます。リソースがノードにキャッシュされている場合ノードはリソースを返し、キャッシュされていない場合はオリジンサーバーに戻って取り出します。

## 設定ガイド

### 設定の確認

[CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、左側のナビゲーションメニューバーで【ドメイン名管理】を選択して、ドメイン名の右側にある【管理】をクリックすると、ドメイン名設定画面に入ります。第3欄の【キャッシュ設定】タブで、【ブラウザのキャッシュ有効期限の設定】セクションを見つけます。
![](https://main.qcloudimg.com/raw/d74acc06100e385c87176d62459f12a6.png)





### ルールの追加

必要に応じてブラウザのキャッシュ有効期限ルールを追加できます。【ルールの追加】をクリックして、ファイルタイプ、ファイルディレクトリ、ファイルパス、ホームページを指定してキャッシュを設定できます。
<img src="https://main.qcloudimg.com/raw/d98a14185f9e9d41d682fb356601e9e5.jpg" style="height:220px"/>

- オリジンサーバーに従う：オリジンサーバーのCache-Controlヘッダーに従います。
- キャッシュ：ブラウザでのリソースのキャッシュ有効期限を設定します。
- キャッシュなし：ブラウザはリソースをキャッシュしません。



**設定の制約**

- 一つのドメイン名には最大20のルールを含めることができます。「すべてのファイル」と「ホームページ」のルールは最大1件まで追加することができます。
- 「すべてのファイル」のルールは削除できませんが、そのキャッシュオプションは変更できます。
- 複数のルールが設定されている場合、ルールの優先順位を変更できます。ルールリストの一番下にあるルールの優先順位が最も高くなります。
- 1つのファイルタイプ/ファイルディレクトリ/ファイルパスの各ルールには、最大50グループのコンテンツを入力でき、異なるコンテンツ間は「;」で区切ります。例：ファイルタイプ - jpg;png。
- 中国語コンテンツはサポートされていません。
