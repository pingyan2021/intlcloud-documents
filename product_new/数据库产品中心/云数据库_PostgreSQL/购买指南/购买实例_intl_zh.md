## 操作场景
本文为您介绍通过腾讯云 PostgreSQL 控制台创建数据库实例的操作。

## 前提条件
已 [注册腾讯云账号](https://intl.cloud.tencent.com/register?s_url=https%3A%2F%2Fintl.cloud.tencent.com%2Fdocument%2Fproduct%2F555%2F30328)。

## 操作步骤
1. 登录 [PostgreSQL 控制台](https://console.cloud.tencent.com/pgsql)，在实例列表单击【新建】。
2. 根据需求指定数据库实例信息。
 - **计费模式**：支持按量计费，即根据使用量计费。
 - **地域**：实例实际部署的地域；建议与需要对接的云服务器保持一致，以便延迟最低。
 - **可用区**：在同一地域内电力和网络互相独立的物理数据中心；建议与需要对接的云服务器保持一致，以便延迟最低。
 - **网络类型**：实例所处的网络，一旦网络选定就不能轻易改变；建议与需要对接的云服务器保持一致，以便延迟最低。
 - **数据库内核版本**：PostgreSQL 的不同数据库内核版本之间存在功能差异，详见：[9.3.5](https://www.postgresql.org/docs/9.3/static/index.html)、[9.5.4](https://www.postgresql.org/docs/9.5/static/index.html)、[10.4](https://www.postgresql.org/docs/10/static/index.html)、[11.8](https://www.postgresql.org/docs/11/index.html) 的官网介绍。
 - **实例规格**：实例规格代表不同的性能水平和价格基数。
 - **硬盘**：默认采用 SSD 盘（本地盘）。
 - **指定项目**：如果您期望不同团队管理不同数据库，请指定到不同团队所处的项目中。
 - **购买数量**：指一次性可购买的实例个数，为避免误操作，我们设置了一次购买上限10个，如果您期望购买更多个数，请多次购买。
3. 确认无误后，单击【立即购买】。
4. 购买后将跳转到支付页面，支付完成后即可返回实例列表页查看到刚购买的实例。

