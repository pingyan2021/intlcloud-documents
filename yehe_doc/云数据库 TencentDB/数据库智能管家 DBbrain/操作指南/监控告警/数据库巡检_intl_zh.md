数据库巡检用于定期自动化全实例健康巡检，用户也可以根据自己的需求个性化设置巡检，帮助用户排查实例隐患并提供解决方案。
>?数据库巡检目前支持云数据库 MySQL（不含基础版）、云数据库 CynosDB（CynosDB for MySQL）。

登录 [DBbrain 控制台](https://console.cloud.tencent.com/dbbrain/patrol)，在左侧导航选择【监控告警】>【数据库巡检】页，在上方选择对应数据库。

## 数据库巡检列表
数据库巡检列表展示了数据库实例所产生的巡检信息汇总，包括实例基本信息、健康等级、慢查询数、大表数量等。

 - 支持用户选择近1天、近3天、近7天及任意时间，查看全实例巡检信息，也支持按实例 ID、健康等级等进行模糊搜索。
 -  单击右上方的【导出】，可以导出数据库巡检全实例的报告信息。
 - “健康等级”列展示通过定时健康巡检所得到的健康等级，等级包括健康、亚健康、危险、高危。
 - 单击“操作”列的【扣分详情】，可查看健康等级的扣分原因，包括诊断项名称、类别、最高严重程度、出现次数及扣分明细，诊断项的详细说明，详见 [异常告警](https://intl.cloud.tencent.com/document/product/1035/37177)。 
 - 单击“操作”列的【查看报告】，可以查看或下载该实例的健康报告。
![](https://main.qcloudimg.com/raw/b557e521bdf20f5bf88c1c2287115168.png)

## 个性化设置
DBbrain 为用户提供了个性化设置功能，单击【个性化设置】，可以跳转至实例管理页设置需要展示的实例，详见 [实例管理](https://intl.cloud.tencent.com/document/product/1035/36033)。
![](https://main.qcloudimg.com/raw/0b71d02259a669e533761c0e0db1d0fe.png)

## 一键开关全实例巡检
DBbrain 为用户提供一键开启和关闭全实例巡检功能，默认关闭，单击【未启用全实例巡检】开关，可以自动开启所有实例的数据库巡检。
![](https://main.qcloudimg.com/raw/7de9b61ab9fa704e63045fd4228ce83d.png)

