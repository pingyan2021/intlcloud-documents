## 設定シナリオ

ご利用のサービスシナリオで、リソースURLパスの大文字と小文字の違いがリソースのコンテンツと関係がない場合は、大文字小文字を区別しないキャッシュ設定を有効にすることで、命中率をある程度向上させることができます。

## 設定ガイド

[CDNコンソール]（https://console.cloud.tencent.com/cdn）にログインし、メニューバーの【ドメイン管理】を選択し、ドメイン名の右側にある【管理】をクリックして、ドメイン名設定画面に入ります。3番目の【キャッシュ設定】列の最下部に【キャッシュの大文字小文字を区別しない】が表示されます。この設定はデフォルトで無効になっています。
![](https://main.qcloudimg.com/raw/95ccb4da3a7589d085658e3965572dee.png)

## 設定例

CDNノードがリソースをキャッシュする際に、Key-Valueの形式でインデックスを作成します。そのKeyはCDNノードのキャッシュキー(Cache Key)となります。フィルタリングパラメータ設定による最適化に加えて、キャッシュの大文字小文字を区別しないを設定することで、最適化することもできます。
例えば、アクセラレーションドメイン名が`cloud.tencent.com`の場合、ユーザーアクセスシナリオは次のようになります。

- ユーザーAが`http://cloud.tencent.com/abc.JPG`のリソースにアクセスします。
- ユーザーBが`http://cloud.tencent.com/abc.jpg`のリソースにアクセスします。
  
A/Bユーザーが同じくCDNノードXにアクセスして、ノードXには上記の2つのリソースのキャッシュがない場合、デフォルトでは、キャッシュの大文字小文字を区別しないは無効になっています。アクセスプロセスは次のようになります。
- ユーザーAがオリジンサーバーにアクセスして`http://cloud.tencent.com/abc.JPG`の画像を取得し、CDNノードXにキャッシュします。対応するキャッシュキーは`http://cloud.tencent.com/abc.JPG`となります。
- ユーザーBオリジンサーバーにアクセスして`http://cloud.tencent.com/abc.jpg`の画像を取得し、CDNノードXにキャッシュします。対応するキャッシュキーは`http://cloud.tencent.com/abc.jpg`となります。
  
キャッシュの大文字小文字を区別しないを有効にすると、上記のシナリオのアクセスプロセスは次のようになります。
- ユーザーAがオリジンサーバーにアクセスして`http://cloud.tencent.com/abc.JPG`の画像を取得し、CDNノードXにキャッシュします。対応するキャッシュキーは`http://cloud.tencent.com/abc.jpg`となります。
- ユーザーBがCDNノードでXが命中したリソースにアクセスし、必要なコンテンツを直接取得します。
