### CDNサービスはリクエスト数に応じた課金に対応しますか。
現在CDNはリクエスト数に応じた課金を対応しません。

### CDNサービスが支払い延滞がある場合、どのような影響が出ますか。
詳細については、課金説明ドキュメントの[支払い延滞に関する説明](https://intl.cloud.tencent.com/document/product/228/2949#.E6.AC.A0.E8.B4.B9.E8.AF.B4.E6.98.8E)をご参照ください 。

### オリジンサーバーがCOSを使用している場合、CDNからCOSへのback-to-originによって生成されたトラフィックに対して課金されますか。
いいえ。CDNからCOSへのback-to-originによって生成されたトラフィックは、CDNではなくCOSによって課金されます。詳細について、[COSをCDNオリジンサーバーとする](https://intl.cloud.tencent.com/document/product/228/32977)をご参照ください。　

### CDNサービスを無効にした後（CDNサービスがオフラインになった後）は、トラフィックと費用は生成しますか。
CDNドメイン名のアクセラレーションサービスを無効にした後、ドメイン名にまだCNAMEが設定されている場合、ノードに解決されたリクエストに対して404ステータスコードが返され、少量のトラフィックが消費されます。コンソールは、お客様の参照用にこの部分のトラフィックデータ記録を保持し、また、対応のログ記録も生成されます。ただし、ドメイン名が無効になっているため、このトラフィックの消費とログパケットに対する課金されません。アクセラレーションサービスを無効にする前に、back-to-origin解析を変更することをお勧めします。　

### CDNでは課金方法をどのように変更しますか。

ご利用中に、ご選択された課金方式が実際の業務状況に適しないと判断された場合（判断方法について、[課金方式の選択](https://intl.cloud.tencent.com/document/product/228/2949#.E8.AE.A1.E8.B4.B9.E6.96.B9.E5.BC.8F.E9.80.89.E6.8B.A9)をご参照ください）、以下の手順に従って課金方式を変更できます。
1. [CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、サービス概要要ページに入り、右側の課金状況の【変更】をクリックします。
![設定画面イメージ](https://main.qcloudimg.com/raw/cfc4ab7bc66b88de437984e438f89a92.png)
2. 元の課金方式**トラフィック課金**から**帯域幅課金**に変更しします。
![設定画面イメージ](https://main.qcloudimg.com/raw/0de03f22b51ab08a545bbfd6717b826b.png)
3. 課金方法を**帯域幅課金**に変更すると、翌日決済時の課金方法は、前日の使用に対応する課金方法が適用されます。

### オリジンサーバーがCVMを使用している場合、CDNからCVMへのback-to-originによって生成されたトラフィックに対して課金されますか。

この部分のトラフィックは、CDNで別途課金されることがありません。

### CDN帯域幅課金の1Gbpsは、何Mbpsに相当しますか。

CDNが使用される帯域幅単位の変換は、1Gbps = 1000Mbps、1Mbps = 1000Kbps、1Kbps = 1000bpsです。

### CDN課金では、ダウンストリームトラフィックのみが計算されますか。

CDNはダウンストリームトラフィックに対してのみ課金し、アップストリームトラフィックに対しては課金しません。

### CDNサービスが攻撃されました。攻撃中に発生したトラフィックの料金を免除できますか。

CDNは本質的にコンテンツの配信を高速化するため、リクエストが悪意のあるものであるかどうかを識別できません。したがって、悪意のあるリクエストを処理して、そのようなトラフィックを発生させないようにすることはできません。悪意のあるドメイン名に起因した過度の損失を回避するために、ドメイン名が攻撃され、帯域幅が10Gbpsを超えた場合、[チケットを送信](https://console.qcloud.com/workorder/category) して、申し立てることができます。Tencent Cloud CDNで帯域幅が10Gbpsを超えた分の費用を計算し、ユーザーに返金します。　

