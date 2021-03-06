本文为您介绍如何通过 Tendis 控制台销毁实例。

## 操作场景
根据业务需求，您可以在控制台自助退还按量计费实例。
- 按量计费实例退还后，实例被移入云数据库回收站保留24小时，期间实例无法访问。如您想恢复该实例，可在回收站进行开机恢复。

自助退还后，实例的状态一旦变为“隔离中”时，就不再产生与该实例相关的费用。
>!
>- 实例销毁后数据将无法找回，备份文件会同步销毁，无法在云上进行数据恢复，请提前做好备份文件的转存。
>- 实例销毁后 IP 资源同时释放。


## 操作步骤
1. 登录 [Tendis 控制台](https://console.cloud.tencent.com/tendis)，选择对应地域，在实例列表选择所需实例，在“操作”列选择【更多】>【销毁】。

>
![](https://main.qcloudimg.com/raw/17be53dac17e4c5dc2170627537d3ed4.png)
2. 在弹出的对话框，确认无误后，单击【销毁】。
>!销毁后所有数据将被清除且不可恢复，请谨慎操作。
>

