## シナリオ

パスワードを忘れた場合は、コンソールでインスタンスのログインパスワードをリセットすることができます。このドキュメントでは、コンソールでインスタンスのログインパスワードをリセットする方法について説明します。
>! 
> - パスワードのリセット操作は、電源がオフになっている状態のインスタンスだけに対して実行できます。
> - 実行中のインスタンスの場合、コンソールでインスタンスのパスワードを変更する際に、サーバーがシャットダウンされますので、データの紛失を避けるために、事前に作業時間を計画しておいてください。影響を最小限に抑えるために、サービス利用量の一番低い時に実行することを推奨します。



## 操作手順

### 単一インスタンスパスワードのリセット

1. [CVMコンソール](https://console.cloud.tencent.com/cvm/index)にログインします。
2. 下図に示すように、インスタンスの管理画面で、パスワードをリセットするCVMの行を選択し、【その他】>【パスワード/キー】>【パスワードをリセット】をクリックします。
![パスワードリセット](https://main.qcloudimg.com/raw/48b4403fe0ba2b8182915cb2d94a88f2.png)
3. ポップアップされた「パスワードをリセット」ウィンドウでは、インスタンスの実行状態に応じてパスワードリセット操作が異なります。詳細は下記の通りです。
 - パスワードをリセットするインスタンスが「**実行中**」の状態である場合、次の手順を実行します。
    1.  「ユーザー名」のタイプを選択し、パスワードをリセットするユーザー名、および対応する「新しいパスワード」を入力し、「パスワードの確認」フィールドに新しいパスワードを再入力して、【次へ】をクリックします。
    2. 下図に示すように、「強制シャットダウンに同意」にチェックを入れて、【パスワードをリセット】をクリックしてリセットを完了します。
![](https://main.qcloudimg.com/raw/7fb5cbfca86cbaf9fd4cec3c15c6d86e.png)
 - パスワードをリセットするインスタンスが「**シャットダウン**」の状態である場合、次の手順を実行します。
    1. 「ユーザー名」のタイプを選択し、パスワードをリセットするユーザー名、および対応する「新しいパスワード」を入力し、「パスワードの確認」フィールドに新しいパスワードを再入力して、【次へ】をクリックします。
    2. 下図に示すように、 【パスワードをリセット】をクリックしてリセットを完了します。
![](https://main.qcloudimg.com/raw/17579c2803867472f283a4afb0d824c5.png)    

### インスタンスパスワードを一括してリセット

1. [CVMコンソール](https://console.cloud.tencent.com/cvm/index)にログインします。
2. 下図に示すように、インスタンスの管理画面でパスワードをリセットするCVMインスタンスにチェックを入れて、上部にある【パスワードをリセット】をクリックします。
![パスワードを一括してリセットする](https://main.qcloudimg.com/raw/a1f607f2f0383c9eab2cbfa800bb15be.png)
3. ポップアップされた「パスワードをリセット」ウィンドウでは、インスタンスの実行状態に応じてパスワードリセット操作が異なります。詳細は下記の通りです。
 - パスワードをリセットするインスタンスが「**実行中**」の状態である場合、次の手順を実行します。
    1.  「ユーザー名」のタイプを選択し、パスワードをリセットするユーザー名、および対応する「新しいパスワード」を入力し、「パスワードの確認」フィールドに新しいパスワードを再入力して、【次へ】をクリックします。
    2. 下図に示すように、「強制シャットダウンに同意」にチェックを入れて、【パスワードをリセット】をクリックします。
![](https://main.qcloudimg.com/raw/ab3e094af0f2ea68d0841bba98d5802a.png)
 - パスワードをリセットするインスタンスが「**シャットダウン**」の状態である場合、次の手順を実行します。
    1. 「ユーザー名」のタイプを選択し、パスワードをリセットするユーザー名、および対応する「新しいパスワード」を入力し、「パスワードの確認」フィールドに新しいパスワードを再入力して、【次へ】をクリックします。
    2. 下図に示すように、 【パスワードをリセット】をクリックしてリセットを完了します。
![](https://main.qcloudimg.com/raw/17579c2803867472f283a4afb0d824c5.png)    
