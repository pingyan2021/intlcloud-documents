## シナリオ
アラームを作成することにより、クラウド製品の状態が変化した際、アラームをトリガーして関連するメッセージを送信します。
各アラームポリシーは、一連のアラームトリガー条件の集合であり、アラームトリガーは「OR」関係になっています。つまり、1つの条件が満たされると、アラームが送信されます。 アラームがトリガーされた直後に、アラームポリシーに関連する全員に送信されます。アラームを受信した後、直ちに確認して適切な措置を講じることができます。アラームを適切に作成することにより、アプリケーションのロバスト性と信頼性を向上させることができます。アラーム情報の詳細については、[アラームポリシーの作成](https://intl.cloud.tencent.com/document/product/248/6215)をご参照ください。

## 前提条件

[クラウド監視コンソール](https://console.cloud.tencent.com/monitor/overview)にログインしました。

## 操作手順
### アラームを作成する
1. 左側のナビゲーションバーで、【 Alarm Configuration】>【[Alarm Policy](https://console.cloud.tencent.com/monitor/policylist)】をクリックして、アラームポリシー管理ページに進みます。
2.【Add】をクリックして、ポリシーを新規作成します。
3.「Create Policy」ページで、ポリシー名を入力し、ポリシータイプ、アラームオブジェクトを選択して、アラームトリガー条件などの情報を設定します。
そのうち、アラームトリガー条件は**指標**、**比較関係**、**しきい値**、**統計期間**、**継続期間**、**繰り返し通知ポリシー**で構成されるセマンティック条件です。
4.【Complete】をクリックします。

### 関連オブジェクト
1. 左側のナビゲーションバーで、【Alarm Configuration】>【[Alarm Policy](https://console.cloud.tencent.com/monitor/policylist)】をクリックして、アラームポリシー管理ページに進みます。
2. アラームポリシー管理ページで、新しく作成されたアラームポリシーをクリックして、アラームポリシー管理ページに進みます。
3. アラームポリシー管理ページで、【Add Object 】をクリックします。
4. ポップアップダイアログボックスで、関連付けする必要のあるCVMを選択し、【 Apply】をクリックします。

### アラーム受信者を設定する
1. 左側のナビゲーションバーで、【Alarm Configuration】>【[Alarm Policy](https://console.cloud.tencent.com/monitor/policylist)】をクリックして、アラームポリシー管理ページに進みます。
2. アラームポリシー管理ページで、新しく作成されたアラームポリシーをクリックして、アラームポリシー管理ページに進みます。
3. アラームポリシー管理ページで、【Alarm Recipient Object】を見つけ、【Edit】をクリックします。
4. ポップアップダイアログボックスで、通知する必要のあるユーザーグループを選択して、【 Save】をクリックします。



