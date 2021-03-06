
业务需要修改数据库实例访问地址时，可使用内网地址转换功能来调整网络。

>!修改实例内网地址属于高危操作，请务必在业务低谷期谨慎操作。修改内网地址后，原地址将持续生效24小时（除非被另外业务占用），请尽快切换业务配置。

## 修改内网地址
VPC 网络下，云数据库支持修改内网地址。
1. 登录 [MariaDB 控制台](https://console.cloud.tencent.com/mariadb)，在实例列表，单击实例名进入实例详情页。
2. 在实例详情页的“内网地址”处，单击 <img src="https://main.qcloudimg.com/raw/071659c8118f8c9b94d4ab90cebbd955.png"  style="margin:0;">图标更改，前提条件是当前子网仍有可用 IP。
![](https://main.qcloudimg.com/raw/5a433d6cb4da6d698127e833a0030682.png)

## 基础网络转 VPC 网络
支持实例从基础网络转入 VPC 网络。
1. 登录 [MariaDB 控制台](https://console.cloud.tencent.com/mariadb)，在实例列表，单击实例名进入实例详情页。
2. 在实例详情页的“所属网络”处，单击【转VPC网络】更改，前提条件是目标 VPC 子网内仍有可用 IP。
>!由于产品支持同城双活架构，建议您优先选择与业务服务器相同，或与主节点所在地域相同的 VPC 子网。

## VPC 网络内子网切换
支持实例在 VPC 网络中切换子网。
1. 登录 [MariaDB 控制台](https://console.cloud.tencent.com/mariadb)，在实例列表，单击实例名进入实例详情页。
2. 在实例详情页的“所属网络”处，单击【更换子网】更改，前提条件是目标 VPC 子网内仍有可用 IP。

