## 概要
ポート53は DNS（Domain Name Server、ドメイン名サーバー）サーバーによって開放され、主にドメイン名の解決に使用されます。DNSサーバーを介してドメイン名とIPアドレス間の変換を実現し、ユーザーはドメイン名を記憶すれば、ウェブサイトに迅速にアクセスできます。

『電気通信業務分類ディレクトリ』（2015 版）は再帰的なインターネットドメイン名解決サービスが電気通信業務に分類しています（コード番号はB26-1）。すなわち、ドメイン名の再帰的なサービスに従事するには、電気通信業務の許可を取得する必要があります。

## 関連する政策と法律規制要件

**1、ビジネスライセンスを取得していない場合、インターネットドメイン名解決サービスに従事することはできません。**
貴社が当該業務に携わっている場合、「エンコードとプロトコル変換業務ライセンス」を取得する必要があり、具体的な取り扱い方法については、所属の省の通信管理局にお問い合わせください。
**『電気通信業務許可の管理措置』第四十六条：**本管理措置の第十六条の第一項規約および第二十八条の第一項規約により、許可されていない電気通信業務または範囲外の電気通信業務に従事している場合、『中華人民共和国の電気通信規則』第六十九条規約に基づく処罰し、状況が深刻な場合、業務中止と命じられ、電気通信業務経営の不正行為リストに加入されます。
**中華人民共和国工業情報化部『インターネットドメイン名の管理措置』第三十六条：**ドメイン名解決サービスを提供する場合、企業は関連法律、規制、基準を順守し、対応する技術、サービス、ネットワークおよび情報セキュリティ保証機能を備え、ネットワークおよび情報セキュリティの安全対策を講じ、法律に従ってドメイン名解決ログ、メンテナンスログ及び変更記録を記録及び保存し、解決サービスの品質と解決システムのセキュリティを保証します。電気通信業務に関与している場合、電気通信業務のビジネスライセンスを法律に従って取得する必要があります。
**2、Tencent Cloudでは、法律に従ってビジネスライセンスを取得していない、または非経営性インターネット情報サービスICP申告手続きを実行する会社または個人にアクセスや料金請求代理などのサービスを提供することはできません。**
**『電気通信業務許可の管理措置』：第二十四条　アクセスサービスを提供する付加価値電気通信事業者は、次の規制を遵守する必要がある：**（三）法律に従ってビジネスライセンスを取得していない、または非経営性インターネット情報サービスICP申告手続きを実行する会社または個人にアクセスや料金請求代理などのサービスを提供することはできません。
個人（会社）は**インターネットドメイン名解決サービス**に従事していない場合、サーバーのセキュリティグループポリシーを調整し、インバウンドルールによってポート53を無効にすることをお勧めします。

## インバウンドルールによるポート53を無効にする手順　

1.  [Tencent Cloud Cloud Virtual Machine コンソール](https://console.cloud.tencent.com/cvm/index)にログインします。
2. インスタンスの管理画面で、ポート53を無効にしたいインスタンスを選択し、当該インスタンスの「ID/名称」をクリックします。下図に示すように：
![](https://main.qcloudimg.com/raw/186bd6ec5c69b12b3ea9645ff1dbb22b.png)
3. インスタンスの詳細画面で、【セキュリティグループ】タブを選択して、インスタンスのセキュリティグループ管理画面に入ります。下図に示すように：
![](https://main.qcloudimg.com/raw/7eb1b0b56520701fc8d28a14cfecd7f1.png)
4.【Bound to security group】フィールドで、変更するインバウンドルールの「セキュリティグループ ID/名称」を選択します。
5.「Security Group Rule」画面で、【Inbound rule】タブを選択し、【Add a Rule】をクリックします。下図に示すように：
![](https://main.qcloudimg.com/raw/f1f7f9ce6d3e259e06542bf19d797022.png)
6. ポップアップした「Add Inbound rule」ウインドウで、以下の情報を入力します。下図に示すように：
![インバウンドルールを追加する-53ポートを無効にする](https://main.qcloudimg.com/raw/f3890575ef22f31f67c0c6902f6df55a.png)
 - Type：「Custom」を選択します。
 - Source：「0.0.0.0/0」を入力します。
 - Protocol port：「UDP:53」を入力します。
 - Policy：「Refuse」を選択します。
7.【Completed】をクリックすると、53ポートが無効になります。

## よくあるご質問

### インターネットドメイン名解決サービスとは。
**インターネットドメイン名解決**は、インターネットドメイン名とそれに対応するIPアドレスの関係を確立します。
**インターネットドメイン名解決サービス**は、インターネット上でドメイン名解決サーバーと関連ソフトウェアを構築することにより、インターネットドメイン名を対応するIPアドレスに変換します。ドメイン名解決サービスには、信頼できる解決サービスと再帰的な解決サービスが含まれます。
- 信頼できる解決サービス：ルートドメイン名、トップレベルドメイン名およびすべてのレベルの他のドメイン名にドメイン名解決サービスを提供することを指します。
- 再帰的な解決サービス：ローカルキャッシュまたは信頼できる解決サービスシステムを照会することにより、ドメイン名とIPアドレス間の対応関係を実現するサービスを指します。

ここでのインターネットドメイン名解決サービスは、特に再帰的な解決サービスを指します。詳細については [『電気通信業務分類ディレクトリ（2015年版）』：B26-1  インターネットドメイン名解決サービス](https://www.miit.gov.cn/zwgk/zcwj/wjfb/tg/art/2020/art_e98406cd89844f7e92ea1bcf3b5301e0.html)をご参照ください。


### インバウンドルールによってポート53を無効にすると、サーバーにどのような影響がありますか。
インターネットドメイン名解決サービスに従事していない場合は、インバウンドルールがポート53を無効にしても、サーバーやビジネスに影響はありません。

### 個人ではインターネットドメイン名解決サービスに従事できますか。
通信サービスプロバイダーは、法律に基づいて設立された会社である必要があります。個人はこのタイプのサービスに従事することはできません。インターネットドメイン名解決サービス業務に従事するには、「エンコードとプロトコル変換ビジネスライセンス」を申請する必要があります。ビジネスライセンス取得の詳細については、通信管理局にお問い合わせください。

### ビジネスライセンスなしでインターネットドメイン名解決サービス業務に従事すると、どのような影響がありますか。
『中華人民共和国の電気通信規則』 第六十九条によると：（一）本規制の第七条第三項、または本規則の第五十八条第（一）項に記載されている行為のいずれかの規定に違反して、許可されていない電気通信業務または範囲外の電気通信業務に従事している場合、国務院の情報産業部門、または省、自治区、および直轄市の電気通信管理機関は、機能と権限に応じて修正を命令し、違法所得を没収、違法所得の3倍から5倍の罰金を科します。違法所得がない、または違法な収入が5万元未満の場合、10万元以上100万元未満の罰金が科せられ、状況が深刻な場合、事業を停止するようと命じられます。

