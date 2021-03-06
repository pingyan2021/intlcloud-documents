<style> 
table th:nth-of-type(1) { width:16%; } 
table th:nth-of-type(2){ width:84%; } 
</style>

CDNサービスをアクティブにした後、[CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、メニューバーで【Domain Management】を選択すると、アクセラレーションドメイン名を追加し、Tencent Cloud CDNが提供するアクセラレーションサービスをご利用いただけます。ドメイン名が追加されると、関連ドメイン名の設定がネットワーク全体のCDNアクセラレーションノードに配信され、実稼働環境でのサービスに直接影響することはありません。アクセラレーションを有効にするには、CNAMEレコードを設定する必要があります。操作手順の詳細については、[CNAMEの設定](https://intl.cloud.tencent.com/document/product/228/3121)をご参照ください。


## ドメイン名の追加
ドメイン名管理ページに入り、【ドメイン名の追加】をクリックします。
![](https://main.qcloudimg.com/raw/02784c06077ee97314ec146aa3369fb1.png)

ドメイン名の追加ページは3つの部分で設定されています。

- ドメイン名属性の設定
- オリジンサーバーの設定
- アクセラレーションサービスの設定

Tencent Cloud CDNは、選択したドメイン名の属性設定とオリジンサーバー設定に基づいて、キャッシュ機能設定を推奨し、変更せずに直接送信できます。

### その1：ドメイン名属性の設定
ドメイン名にお客様のサービスのサービスドメイン名を入力し、そのプロジェクト、アクセラレーションリージョン、およびサービスタイプを選択します。
![](https://main.qcloudimg.com/raw/4f2de8b5158a317b1913bd5f920dbf3b.png)

**設定項目の詳細説明：**

| 設定項目   | 説明                                                     |
| -------- | ------------------------------------------------------------ |
| ドメイン名     | 1. ドメイン名の長さは50文字以内です。<br/>2. ドメイン名は工信部にてICP申告済みのものです。<br/>3.ドメイン名がa.test.com、a.b.test.com などの形式のサブドメイン名、または\*.test.com、\*.a.test.com 形式の汎用ドメイン名となります。<br/>4.ドメイン名が汎用ドメイン名であるか、または他のユーザーからアクセスされている場合は、ドメイン名にアクセスまたは取得する前に[所有権の検証]（#m1）を行う必要があります。<br/><br/><strong>注意事項：</strong><br/>1. 汎用ドメイン名にアクセスした後、現在はサブドメイン名またはレベル2の汎用ドメイン名である場合は他のアカウントにアクセスできません。<br/>2. 現在、‵*.test.com ‵と‵ *.a.test.com‵ が同時にアクセスすることはできません。|
| 所属プロジェクト | プロジェクトは、Tencent Cloudのすべてのクラウドサービスの共有リソースセットの概念です。[プロジェクト管理](https://console.cloud.tencent.com/project)ページでプロジェクト関連の操作を実行できます。|
| アクセラレーションリージョン | 中国国内：グローバルユーザーからのアクセスは、中国国内のアクセラレーションノードにスケジューリングされてサービスを提供します。<br/>中国国外：グローバルユーザーからのアクセスは、中国国外のアクセラレーションノードにスケジューリングされてサービスを提供します。<br/>グローバル：グローバルユーザーからのアクセスは、最も近いノードにスケジューリングされてサービスを提供します。<br/><br/><strong>注意事項：</strong><br/>中国国内と中国国外アクセラレーションサービスは別々で課金されます。課金ポリシーの詳細について[クリックして確認](https://intl.cloud.tencent.com/document/product/228/2949)してください。|
｜サービスタイプ| Tencent Cloud CDNでは、異なるサービスタイプに相応しいアクセラレーションパフォーマンスの最適化が行われています。<br/>より良いアクセラレーション効果を得るには、ご自分のサービスに近いサービスタイプを選択することをお勧めします。<br/><br/>静的アクセラレーション：電子商取引、Webサイト、ゲーム画像系の小規模リソースアクセラレーションシナリオに適しています。 <br/>ダウンロードアクセラレーション：ゲームのインストールパッケージ、音声・動画ソースファイルのダウンロード、携帯電話のファームウェア配布などのダウンロードシナリオに適しています。<br/>ストリーミングメディアVODのアクセラレーション：オンライン教育、オンライン動画オンデマンドなどに適しています。|
| タグ | 最大50個のタグを追加できます。<br/>既存のタグの選択のみをサポートします（タグコンソールで追加されたタグ）。<br/>タグを追加するには、タグキーとタグ値が必要です。未選択はできません。[タグ管理](https://console.cloud.tencent.com/tag/taglist) でタグの関連操作が行えます。 |
| アクセラレーションプロトコル | IPv4：ノードはIPv4アクセスのみをサポートします。<br/>IPv4 + IPv6：ノードはIPv4とIPv6の両方のアクセスをサポートしています。このオプションにチェックを入れた場合のみ、IPv6オリジンサーバーを設定できます。<br/><br/><strong>注意事項：</strong><br/>IPv6は、中国国内でのみサポートされています。 |

### その2：オリジンサーバーの設定

サービスオリジンサーバー関連情報を設定します。CDNノードはキャッシュにリソースがない場合、オリジンサーバーに戻って取り出してキャッシュします。
![](https://main.qcloudimg.com/raw/4a051cfc61dbd0e64b5ccfb8b386829d.png)

**設定項目の詳細説明：**

| 設定項目   | 説明                                                     |
| -------- | ------------------------------------------------------------ |
| オリジンサーバータイプ |ユーザー保有オリジンサーバー：安定したビジネスサーバー（オリジンサーバー）がすでにある場合は、これを選択します。<br/><a href = "https://intl.cloud.tencent.com/product/cos">COSオリジンサーバー</a>：リソースがすでにCOSに保存されている場合、直接バケットを選択してオリジンサーバーとすることができます。|
| オリジンサーバーアドレス | ユーザー保有オリジンサーバー：<br/>1. 複数のIPをオリジンサーバーとして設定することができます。back-to-originするときに、back-to-origin中にポーリングされます。<br/>2. 構成ポート（0-65535）と重み（1-100）の追加をサポート：`オリジンサーバー：ポート：重み`（ポートは省略でき、`オリジンサーバー::重み`）で、 HTTPSプロトコルは現在、ポート443のみをサポートしています。<br/>3. ドメイン名をオリジンサーバーとして設定することができます。このドメイン名は、ビジネスアクセラレーションドメイン名とは異なる必要があります。|
| back-to-originプロトコル | オリジンサーバーでサポートされているプロトコルに基づいて選択できます。<br/>HTTP：HTTP / HTTPSアクセス要求はHTTP back-to-originを使用します。<br/>HTTPS：HTTP / HTTPSアクセス要求はHTTPS back-to-originを使用します。（オリジンサーバーはHTTPSアクセスをサポートする必要があります）。<br/>Follow protocol：HTTPアクセス要求はHTTP back-to-originを使用します。HTTPSアクセス要求はHTTPS back-to-originを使用します。（オリジンサーバーはHTTPSアクセスをサポートする必要があります）。 |
| back-to-originドメイン名 | back-to-originドメイン名とは、CDNノードがback-to-originするときに、オリジンサーバーでアクセスしたサイトのドメイン名のことです。<br/>サブドメイン名にアクセスする場合、デフォルトはアクセラレーションドメイン名と同じで、カスタマイズして変更できます。<br/>汎用ドメイン名にアクセスする場合、デフォルトでは実際にアクセスするサブドメイン名となります。カスタマイズして変更できます。|

### その3：アクセラレーションサービスの設定
ノードアクセラレーションサービス関連の設定を行います。
![](https://main.qcloudimg.com/raw/fc616c71acf52fe77af7ce08d9773ad4.png)

**設定項目の詳細説明：**

| 設定項目   | 説明                                                     |
| :------- | :----------------------------------------------------------- |
| 基本設定 | ノードがリソースをキャッシュするには、Key-Valueマッピングに従います。ここでのKeyはリソースURLです。フィルタリングパラメータを有効にすると、KeyはURLの「?」以降のパラメータを無視してマッピングします。フィルタリングパラメータを有効にしないと、Keyは完全なリソースURLになります。静的アクセラレーションタイプは、デフォルトでは無効になっており、ダウンロードおよびストリーミングメディアVODアクセラレーションタイプは、デフォルトでは有効になっています。|
| Range back-to-origin | back-to-origin時にパート化するかどうかを設定します。オリジンサイトはRangeリクエストをサポートしている必要があります。対象オリジンサーバーまたはサービスタイプがストリーミングメディアVODアクセラレーションである場合、Range back-to-originがデフォルトで有効になっています。 |
| キャッシュルール | これは、ノードキャッシュの有効期限の設定を指します。静的アクセラレーションの場合、すべてのファイルのキャッシュ有効期限は、デフォルトでオリジンサーバーに従います。ダウンロードおよびストリーミングメディアVODアクセラレーションの場合、すべてのファイルのキャッシュ有効期限はデフォルトで30日です。設定されたノードキャッシュの有効期限は最長有効期限であり、ノードのストレージリソースの影響を受けます。実際のキャッシュ時間は、状況に応じて定めます。 |

## 設定の完了

【送信を確認】をクリックし、ドメイン名を追加します。ドメイン名の設定をネットワーク全体のノードに配信するには約5～10分かかります。しばらくお待ちください。
![](https://main.qcloudimg.com/raw/0eb54022c36df808aabe5fb4c2838c77.png)

## 後続の操作
>アクセスが完了した後、Tencent Cloud CDNは対応するCNAMEアドレスをアサインします。CDNサービスを有効にするには、まずCNAMEを設定する必要があります。詳細については、[CNAMEの設定](https://intl.cloud.tencent.com/document/product/228/3121)をご参照ください。

<span ID ="m1"></span>
## ドメイン名所有権の検証
アクセスするドメイン名が汎用ドメイン名であるか、他のユーザーからすでにアクセスされている場合、ドメイン名にアクセスまたは取得する前に、ドメイン名の所有権を認証する必要があります。ドメイン名の所有権の認証方式はDNS認証となります。認証手順は次のとおりです。

1. 【検証方法】をクリックして、DNS検証に追加する解析記録情報を取得します。認証が完了するまでページを閉じないでください。
   ![img](https://main.qcloudimg.com/raw/a0bae11cfa188a1ec2a6ca3d5cd4edec.png)
2. ドメイン名リゾルバで、レコードタイプがTXTのDNSレコードを追加し、ホストレコードに_cdnauthを入力します。レコード値は、検証方法ページでランダムに生成されたレコード値です。
3. TXT解析が有効になるのを待ち、【認証】ボタンをクリックして確認します。「認証に失敗しました」と表示された場合は、DNSレコードが有効になってからもう一度試して、TXTレコードが正しく入力されているかどうかを確認します。
