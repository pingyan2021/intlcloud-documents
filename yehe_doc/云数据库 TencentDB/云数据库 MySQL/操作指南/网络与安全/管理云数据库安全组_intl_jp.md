## 操作シナリオ
[セキュリティグループ](https://cloud.tencent.com/doc/product/213/500)は1台又は複数台のCDBのネットワークアクセス制御を設定するための、ステートフルなフィルタリング機能を含む仮想ファイアウォールで、Tencent Cloudの重要なネットワークセキュリティの分離手段です。セキュリティグループは論理上のグループで、同一地域内の同じネットワークセキュリティ分離ニーズを有するCDBインスタンスを同一セキュリティグループ内に加えることができます。CDBはCloud Virtual Machineなどとセキュリティグループリストを共有し、セキュリティグループ内は規則に基づいてマッチングされます。

>?
>- MySQLセキュリティグループは現時点でVirtual Private Cloud（VPC）のプライベートネットワークアクセスと外部ネットワークアクセスのネットワーク制御のみをサポートしますが、基幹ネットワークへのネットワーク制御はサポートしません。
>- 広州、上海、中国香港、北京、成都、重慶、ソウル、東京地域のみがデータベースの外部ネットワークアクセスのセキュリティグループ機能をサポートし、その他の地域は現在サポートしていません。
>- CDBには自発的なアウトバウンドトラフィックがないため、アウトバウンド規則はCDBに対して無効です。
>- MySQLセキュリティグループはマスターインスタンス、読取専用インスタンス、災害復旧インスタンスをサポートします。
>- MySQLの基本バージョンはセキュリティグループをサポートしていません。


## CDBにセキュリティグループを構成する
### ステップ1：セキュリティグループの作成
1. [CDBコンソール](https://console.cloud.tencent.com/cvm/securitygroup)にログインします。
2. 左側のナビゲーションバーで【セキュリティグループ】ページを選択し、地域を選択して、【新規作成】をクリックします。
3.　ポップアップされたのダイアログボックスで、以下の構成を完了し、確認後に【確定】をクリックします。
 - テンプレート：セキュリティグループ中のデータベースインスタンスがデプロイする必要のあるサービスに基づき、適切なテンプレートを選択し、セキュリティグループ規則の構成を簡略化します。以下の表に示すとおりです。
<table>
	<tr><th>テンプレート</th><th>説明</th><th>説明</th></tr>
	<tr><td>すべてのポートを開放</td><td>デフォルトではすべてのポートをパブリックネットワークとプライベートネットワークに開放し、一定のセキュリティリスクがあります。</td><td>-</td></tr>
	<tr><td>22、80、443、3389ポートとICMPプロトコルを開放</td><td>デフォルトで22、80、443、3389ポートとICMPプロトコルを開放し、プライベートネットワークはすべて開放されています。</td><td>このテンプレートはCDBに対して無効です。</td></tr>
	<tr><td>カスタマイズ</td><td>セキュリティグループの作成が完了後、必要に応じてセキュリティグループ規則を自ら追加します。具体的な操作は、以下の「セキュリティグループ規則の追加」を参照してください</a>。</td><td>-</rd></tr>
</table>
 - 名称：セキュリティグループ名称をカスタマイズで設定します。
 - 所属プロジェクト：デフォルトで「デフォルトプロジェクト」を選択されていますが、後で管理しやすいようにその他のプロジェクトを指定することができます。
 - 備考：カスタマイズについては、後で管理しやすいようにセキュリティグループを簡単に記述します。


 <span id="Step2"></span>
### ステップ2：セキュリティグループ規則の追加
1. [セキュリティグループページ](https://console.cloud.tencent.com/cvm/securitygroup)で規則を設定する必要のあるセキュリティグループの行で、操作列の【規則の修正】をクリックします。
2. <span id="step02">セキュリティグループルールページで、【インバウンドルール】>【ルールの追加】を選択します。</span>
3.　ポップアップされたダイアログボックスで、規則を設定します。
 - タイプ：デフォルトでは「カスタマイズ」が選択されていますが、その他のシステムの規則のテンプレートを選択することもできます。MySQL(3306)テンプレートを選択することをお勧めします。
 - ソース：トラフィックのソース（インバウンド規則）又はターゲット（アウトバウンド規則）については、下記選択肢のいずれか1つを指定してください。
<table>
	<tr><th>指定のソース/ターゲット</th><th>説明</th></tr>
	<tr><td>単一IPv4 又はIPv4アドレス範囲は</td><td>CIDR表記法を使用します（例：<code>203.0.113.0</code>、<code>203.0.113.0/24</code>又は<code>0.0.0.0/0</code>。そのうち、<code>0.0.0.0/0</code>はすべてのIPv4アドレスにマッチングしていることを表します）。</td></tr>
	<tr><td>単一IPv6 又はIPv6アドレス範囲は</td><td>CIDR表記法を使用します（例：<code>FF05::B5</code>、<code>FF05:B5::/60</code>、<code>::/0</code>又は<code>0::0/0</code>そのうち、<code>::/0</code>又は<code>0::0/0</code>はすべてのIPv6アドレスにマッチングしていることを表します）。</td></tr>
	<tr><td>セキュリティグループIDの引用については、以下のセキュリティグループのIDを引用することができます：<ul  style="margin: 0;"><li>セキュリティグループID</li><li>その他のセキュリティグループ</li></ul>
</td><td><ul  style="margin: 0;"><li>現在のセキュリティグループは、セキュリティグループと関連付けられているCloud Virtual Machineを表します</li><li>その他のセキュリティグループは、同一エリア中の同一プロジェクト下の別のセキュリティグループIDを表します。</li></ul>
</td></tr>
	<tr><td><a href="https://intl.cloud.tencent.com/document/product/215/31867">パラメーターテンプレート</a>中のIPアドレスオブジェクト又はIPアドレスグループオブジェクトを引用します</td><td>-</td></tr>
</table>
 - プロトコルポート：プロトコルタイプとポート範囲を記入します。[パラメータテンプレート](https://intl.cloud.tencent.com/document/product/215/31867)の中のプロトコルポート又はプロトコルポートグループを引用することもできます。
  >? MySQLの接続には、プロトコルポート3306を有効化しなければなりません。
 - ポリシー：デフォルトで「許可」を選択します。
    - 許可：このポートに対応するアクセスリクエストをパスします。
    - 拒否：データパケットを直接破棄し、いかなる応答情報も戻しません。
 - 備考：カスタマイズについては、後で管理しやすいように規則を簡単に記述します。
4. <span id="step04">【完了】をクリックし、セキュリティグループのインバウンド規則の追加を完了します。</span>

#### 事例
**シナリオ：**MySQLを作成し、Cloud Virtual Machine（CVM）を介してMySQLにアクセスすることを希望する場合。
**解決方法：**セキュリティグループ規則を追加する時、【タイプ】からMySQL(3306)を選択し、プロトコルポート3306を有効化します。
実際のニーズに基づきすべてのIP又はIP（IPセグメント）を指定してインターネットにオープンすることもできます。構成はCVMを介してMySQLのIPソースにアクセスすることができます。

| 方向 | タイプ | ソース | プロトコルポート | ポリシー |
|---------|---------|---------|---------|---------|
| インバウンド | MySQL(3306)  | すべてのIP：0.0.0.0/0<br>IPを指定：指定するIP又はIPセグメントを入力します | TCP:3306 | 許可 |
               

### ステップ3：セキュリティグループの構成
セキュリティグループはTencent Cloudより提供されるインスタンス級のファイアウォールです。CDBのインバウンドトラフィック制御を行うことができます。インスタンスを購入する際にセキュリティグループをバインディングすることも、インスタンスを購入した後にコンソールでセキュリティグループをバインディングすることもできます。

>!現在、MySQLセキュリティグループは**Virtual Private Cloud CDB**の構成のみをサポートしています。

1.  [MySQLコンソール](https://console.cloud.tencent.com/cdb)にログインします。 インスタンスリストで、インスタンス名をクリックしてインスタンス管理ページに入ります。
2. 【セキュリティグループ】タブを選択し、【セキュリティグループの構成】をクリックします。
3. 表示されたダイアログボックスで、バインドするセキュリティグループを選択し、【OK】をクリックします。

## セキュリティグループ規則のインポート
1. [セキュリティグループページ](https://console.cloud.tencent.com/cvm/securitygroup)で必要なセキュリティグループを選択し、セキュリティグループID/名称をクリックします。
2. インバウンド/アウトバウンド規則タブで【規則のインポート】をクリックします。
3. ポップアップされたダイアログボックスで、編集したインバウンド/アウトバウンド規則テンプレートファイルを選択し、【インポートを開始する】をクリックします。
> ?規則をインポートする必要のあるセキュリティグループに既にセキュリティグループ規則が存在している場合、先に既存の規則をエクスポートすることをお勧めします。そうでない場合、新しい規則をインポートする時に元の規則が上書きされてしまいます。
	

## セキュリティグループのクローン
1. [セキュリティグループページ](https://console.cloud.tencent.com/cvm/securitygroup)にて、リストの操作列で【その他】>【クローン】を選択します。
2. ポップアップされたダイアログボックスで、ターゲット地域、ターゲットプロジェクトを選択した後、【確定】をクリックします。新しいセキュリティグループをCVMに関連付ける必要がある場合、セキュリティグループ内のCloud Virtual Machineをもう一度管理してください。

## セキュリティグループの削除
1. [セキュリティグループページ](https://console.cloud.tencent.com/cvm/securitygroup)にて、削除する必要のあるセキュリティグループを選択し、操作列で【その他】>【削除】を選択します。
2. ポップアップされたダイアログボックスで、【確定】をクリックします。現在のセキュリティグループに関連付けられたCVMがある場合、削除前にセキュリティグループを解除する必要があります。

