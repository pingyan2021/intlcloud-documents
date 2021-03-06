## ユースケース

サービス移行はTencent Cloudが企業ユーザー向けに開発した移行プラットフォームです。この移行プラットホームはソース側ホストのOS、アプリケーションやアプリケーションデータなどをCloud Virtual MachineまたはCloud Block Storageに移行させることにより、企業のクラウド化、クロスクラウドプラットフォームの移行、クロスアカウント/リージョンの移行またはハイブリッドクラウドのデプロイなどのビジネスニーズに対応できます。

サービス移行は、オフライン移行とオンライン移行に分かれています。オフライン移行は下記の2種類があります。
- [オフラインでのインスタンス移行](#cvmStep)では、システムディスクイメージを指定したCVMに移行することです。
- [オフラインでのデータ移行](#csmStep)では、データディスクイメージを指定したCloud Block Storageに移行することです。

## 前提条件

オフライン移行はCloud Object Storage（COS）のサポートが必要です。お客様が所在するリージョンがCOSの対応範囲にあることを確保してください。
現在、COSでサポートされるリージョンの詳細については、 [リージョンおよびアクセスドメイン名](https://intl.cloud.tencent.com/document/product/436/6224)をご参照ください。

## 準備事項

> 
> - 現在、Tencent Cloudのサービス移行はqcow2、vpc、vmdk、rawのイメージ形式に対応しています。転送と移行の時間を短縮するように、圧縮されたイメージ形式のご利用をお勧めします。
> - イメージをアップロードするCOSリージョンは、移行先のCVMリージョンと一致させる必要があります。
> - オフライン移行の場合、アップロードされたイメージファイルのサイズは、移行先のディスク容量より大きくてはなりません。イメージファイルのサイズが50 GBの場合、移行先システムディスクには少なくとも50 GBの容量が必要です。
> - フライン移行はスナップショットファイル（ファイル名が\*-00000\*.vmdkのようなスナップショットファイル）の移行をサポートしません。

- イメージ作成ドキュメントに基づいて、移行するサーバのイメージファイルを作成してください。
 - Windowsの場合は、 [Windowsイメージの作成](https://intl.cloud.tencent.com/document/product/213/17815)をご参照ください。
 - Linuxの場合は、[Linuxイメージの作成](https://intl.cloud.tencent.com/document/product/213/17814)をご参照ください。
- 作成したイメージファイルをCOSにアップロードします。  
 - イメージファイルは通常サイズが大きく、Webページを介したイメージのアップロードが中断しやすいため、COSCMDを利用してイメージをアップロードすることをお勧めします。操作の詳細については、[COSCMDツールドキュメント](https://intl.cloud.tencent.com/document/product/436/10976)をご参照ください。  
 - ほかのクラウドプラットフォームからエクスポートしたイメージが圧縮パッケージ形式（例えば.tar.gz）の場合は、解凍する必要がなく、直接にCOSにアップロードして移行できます。
- イメージをアップロードするCOSアドレスを取得します。
 [Cloud Object Storageコンソール](https://console.cloud.tencent.com/cos5/bucket) で、先ほどアップロードしたイメージファイルを見つけ、ファイル情報を確認し、ファイルリンクを取得します。
- 移行先のCVMまたはCBSを用意します。
[ここをクリックしてCVMを購入する >>](https://buy.cloud.tencent.com/cvm?tab=custom&step=1&regionId=8)
[ここをクリックしてCBS購入ガイドへ >>](https://intl.cloud.tencent.com/document/product/362/32414)


## 操作手順

<span id="cvmStep"></span>
### オフラインでのインスタンス移行

1. CVMコンソールにログインして、左側のナビゲーションメニューバーで、【[サービス移行](https://console.cloud.tencent.com/cvm/csm/index?rid=4)】をクリックします。
2. 【インスタンス移行の新規作成】をクリックします。
3. 移行の準備が完了してから、【次へ】をクリックします。
4. 下図に示すように、リージョンを選択し、タスク名、COSリンク、移行先のCVMインスタンスなどの移行構成情報を完成させます。【完了】をクリックすると、移行タスクが正常に作成されます。
下図に示すように、オフラインデータ移行の管理ページに戻り、移行タスクの進行状況を確認します。
>  
> - COSファイルは先に [パブリック読み取り・プライベート書き込み権限](https://intl.cloud.tencent.com/document/product/436/13327)を設定する必要があります。
> - 移行先のインスタンスのシステムディスクの容量がアップロードされたイメージファイルのサイズより小さくすることはできません。そうでない場合、タスクは失敗します。
> 

<span id="csmStep"></span>
### オフラインでのデータ移行

1. CVMコンソールにログインして、左側のナビゲーションメニューバーで、【[サービス移行](https://console.cloud.tencent.com/cvm/csm/index?rid=4)】をクリックします。
2.【データ移行の新規作成】をクリックします。
3. 移行の準備が完了してから、【次へ】をクリックします。
5. リージョンを選択して、タスク名称、COSリンクと移行先のCBSなどの移行構成情報を完成させます。【完了】をクリックすると、移行タスクが正常に作成されます。
> 移行先のCBS容量は、アップロードされたイメージファイルのサイズより小さくすることはできません。そうでない場合、タスクは失敗します。
>

## よくあるご質問

詳細については、[サービス移行について](https://intl.cloud.tencent.com/document/product/213/32395)をご参照ください。

