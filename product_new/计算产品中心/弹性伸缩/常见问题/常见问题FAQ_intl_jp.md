### 1.クールダウン時間とは？
クールダウン時間とは、同じスケーリンググループで実行されたスケーリングアクティビティ（CVMインスタンスの追加または除去）の終了後のロック時間のことです。この期間内に、スケーリンググループはスケーリングアクティビティを実行しません。クールダウン時間の値は0〜999999（秒）に指定可能です。

### 2. 手動で追加したCVMはクールダウン時間の対象ですか？
手動で追加したCVMはクールダウン時間の対象外です。

### 3.Auto Scalingに料金がかかりますか？
Auto Scaling機能は無料で使用可能です。遠慮なくご利用ください。
Auto Scalingによって自動的に作成されたCVMインスタンスは通常の従量制で課金されます。手動で追加したCVMインスタンスは元の課金制で課金され、スケーリンググループへの追加または除去による影響を受けません。

### 4.どうすればスケーリンググループ内にあるCloud Virtual Machineの最大数を増やすのか？
Auto Scalingのスケーリンググループは、最大で2000台のCVMをサポートできます。現在、Tencent Cloudユーザーの各アベイラビリティゾーンで保有できる従量課金タイプのCVMクォータについては、[従量課金のCVMインスタンスの購入に関する制限](https://intl.cloud.tencent.com/document/product/213/2664)を参照してください。スケーリンググループに2000台以上のCVMが必要な場合、またはアベイラビリティゾーンで固定クォータを超えた従量課金のCVMを使用したい場合は、[作業依頼書をサブミット](https://console.cloud.tencent.com/workorder/category/create?level1_id=6&level2_id=7&source=0) にアクセスして、申請してください。

### 5.どのようなマシンがAuto Scalingに適しますか？
スケーリンググループ内のCloud Virtual Machineインスタンスにデプロイされているアプリケーションは、状態無しかつ交換可能である必要があります。スケーリンググループ内のインスタンスはスケールイン時に回収される可能性があるため、Auto ScalingのCVMインスタンスはアプリケーションの状態情報（セッションなど）および関連データ（データベース、ログなど）を保存できません。アプリケーションの状態情報を保存する必要のある場合は、スケーリンググループ以外の独自のCloud Virtual Machineに状態情報を保存することができます。

### 6.スケーリンググループにCloud Virtual Machineを手動で追加するための要件は何ですか？
スケーリンググループにCloud Virtual Machineを手動で追加するには、次の要件が必要です：
-スケーリンググループと同じゾーンに存在しています；
- ネットワーク環境（VPCまたは基幹ネットワーク）は、スケーリンググループと一致しています；
- 動作中の状態にあります。

### 7. スケーリンググループにアソシエイトされたCloud Load Balancerインスタンスの要件は何ですか？
スケーリンググループにアソシエイトされるCloud Load Balancerインスタンスは、スケーリンググループと同じネットワーク環境（VPCまたは同一地域の基幹ネットワーク）にある必要があります。


### 8.Auto Scalingは、CVMの構成を自動的に調整できますか？
Auto Scalingは、ユーザーのサービスニーズとポリシーに基づいて、リソースの弾性コンピューティングを自動的に調整する管理サービスです。サービスの増加に応じてCVMインスタンスを自動的に増加し、サービスの減少に応じてCVMインスタンスを自動的に減少できます。現在、Auto Scalingは「スケールアップ」をサポートしていません。つまり、Auto ScalingはCVMのCPU、メモリ、帯域幅を一時的に自動的に増減できません。

### 9.Cloud Load Balancerとクラウド監視と連携してAuto Scalingを使用する必要がありますか？
Auto Scalingは、Cloud Load Balancerを使用するかどうかに関係なく、CVMインスタンスを単独でスケールアウトまたはスケールインできます。

### 10.一定の時間内にCVMを一括でスケールアウトする必要がある場合、どのように設定しますか？
ユーザーは1ペアの定時タスクを設定できます：1つの定時タスクはスケールアウト操作を定義し、期待するインスタンス数をスケールアウトする数に設定します。もう1つの定時タスクはスケールイン操作を定義し、期待するインスタンス数をスケールインする数に設定します。
詳細については、[最良事例 >>](https://intl.cloud.tencent.com/document/product/377/8617)を参照してください

### 11.スケーリンググループの除去ポリシーの具体的なルールは何ですか？
Tencent CloudのAuto Scalingは下記2つの除去ポリシーをサポートしています：
-最も古いマシンの削除：自動的に追加された最も古いマシンを削除します。自動的に追加されたマシンが削除された後、手動で追加した最も古いマシンを削除します。
-最新のマシンの削除：自動的に追加された最新のマシンを削除します。自動的に追加されたマシンが削除された後、手動で追加した最新のマシンを削除します。

### 12.アラームポリシーはクラウド監視情報をどのように統計しますか？
最大値を例に説明します。最大値統計の基本的なポリシーは、各周期は各Cloud Virtual Machineに設定された監視項目に対して、1分ごとの値（1分ごとに1つの値を取得する）を取得し、取得された値が連続する複数の期間（期間の数はユーザーカスタマイズ可能）にわたって設定したルールを満たしている場合、アラームのスケーリングアクティビティがトリガーされます。

たとえば、スケーリンググループに5つのCVMがある場合、アラームスケーリングポリシーは、「CPU利用率が3つの連続した期間で50％を超えている」に定義されます。システムは各CVMに対し、1分ごとに1つの値を取得します。つまり、1つの期間（5分間）で25個のCPU利用率の値を取得することになります。25個の値のなかにしきい値（50％）を超えた値が存在する場合、当該期間はアラームスケーリングのルールを満たしています。3つの連続した期間がこのルールを満たしている場合、スケーリングアクティビティがトリガーされます。

### 13. 期待するインスタンス数とは？
期待するインスタンス数は、現在のスケーリンググループに対する適切なインスタンス数であり、値の範囲は最小スケーリング数と最大スケーリング数の間です。期待するインスタンス数を手動で調整したり、定時タスクとアラームスケーリングタスクで調整をトリガーしたりすることができます。スケーリンググループは、インスタンスの実際数が期待するインスタンス数に一致するように自動的に調整できます。
-スケーリンググループを作成するとき：ユーザーがスケーリンググループを作成する際にインスタンスの初期数を設定した場合、期待するインスタンス数はインスタンスの初期数です。
-アラームスケーリングタスクによる調整：アラームスケーリングがトリガーされたとき、スケーリンググループは現在のインスタンス数を期待するインスタンス数に調整します。たとえば、トリガーアクションが2台のCloud Virtual Machineの追加である場合、バックグラウンドで期待するインスタンス数の現在数に2をプラスすることにより、追加が実現されます。システムは、スケーリンググループの現在のインスタンス数が期待するインスタンス数と一致していないことを検出した場合、現在のインスタンス数が期待するインスタンス数と一致するように2台のCloud Virtual Machineを追加します。
-期待するインスタンス数の定期または手動調整：ユーザーが定時タスクで調整するか、直接修正することで期待するインスタンス数を変更した場合、システムは現在のインスタンス数が期待するインスタンス数と一致していないことを検出し、期待するインスタンス数と一致するまでスケーリングを行います。
-システム調整：期待するインスタンス数は、インスタンスの最大数と最小数の間です。インスタンスの最大数または最小数が変化すると、期待するインスタンス数も変化する可能性があります。たとえば、期待するインスタンス数が3、スケーリング最小数が2、スケーリング最大数が5です；スケーリング最小数が4に調整されると、スケーリング最小数に一致するために期待するインスタンス数は4に調整されます。

### 14.スタートアップコンフィギュレーションでデータディスクのスナップショットが指定されている場合、何に注意する必要がありますか？
スタートアップコンフィギュレーションでデータディスクのスナップショットが指定されている場合、スケーリンググループが自動的にスケールアウトを行えるように、データディスクが正確かつ自動的にマウントできることを確保する必要があります。新しいCloud Virtual Machineインスタンス起動時のデータディスクの自動マウントを可能にするために、Auto Scalingを設定する前にデータディスクのスナップショットの元インスタンスに対して、いくつかの操作を実行する必要があります。
操作の詳細については、[Cloud Block Storageのマウント](https://intl.cloud.tencent.com/document/product/362/5745)を参照してください。

### 15.スケーリンググループが無効化されると操作がどのような操作が一時停止しますか？
スケーリンググループが無効に設定された後、自動的にトリガーされるアクティビティは発生しませんが、スケーリンググループの制限が依然として有効になっています。
スケーリンググループが無効に設定された後、下記の自動操作は実行しません。
-アラームスケーリング。
-定時タスク。
-ヘルスチェック。
-手動操作によるインスタンスの現在数と期待するインスタンス数との不一致の発生。

ただし、サービスの正常な実行を確保するために、下記のスケーリンググループの基本的な制限がなお存在しています。
- 手動で除去する際に「min」よりも小さい場合、除去ができません。
- 手動で追加する際に「max」よりも大きい場合、追加ができません。
- スケーリングアクティビティをトリガーすることなく、手動で「min」または「max」を増やします。

### 16.スケーリンググループに自動的に追加するCloud Virtual Machineのライフサイクルのフェーズは何ですか？
- Creating 作成中：CVMが作成しています
- InService 動作中：CVMが動作しています
- Removing 除去中：CVMが除去されています
- Attaching バインディング中：CVMがスケーリンググループにバインディングされています
- Detaching バインド解除中：CVMがスケーリンググループからバインド解除されています
- AttachLb LBのバインディング中：LBがCVMにバインディングされています
- DetachLb LBのバインド解除中：LBがCVMからバインド解除されています
- Preheating 準備中：CVMが準備しています


### 17. CVMの除去ルール
- 手動で追加したCVMの除去：除去されたCVMはスケーリンググループの管理対象外となり、ASによって削除されず、また、LBからバインド解除されません
- 自動スケールアウトで追加されたCVMの除去：CVMは廃棄され、LBからバインド解除されます
