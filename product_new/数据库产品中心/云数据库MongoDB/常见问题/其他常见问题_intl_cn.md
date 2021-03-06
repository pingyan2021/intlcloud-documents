### MongoDB 的最新版本号是多少？
腾讯云数据库 MongoDB 目前提供的版本是3.2.10和3.6.3。

### MongoDB 云数据库怎么删除，到期后不续费会自动删除吗？
云数据库 MongoDB 实例到期后不续费会自动销毁，请您确认并备份数据。您可在控制台实例列表，选择【操作】>【更多】>【退货退费】执行自助销毁操作。

### MongoDB 如何申请安全凭证？
第一次使用云 API 之前，您需要在腾讯云 CVM 控制台上申请安全凭证。
安全凭证包括 SecretId 和 SecretKey：
 - SecretId：用于标识 API 调用者身份。
 - SecretKey：用于加密签名字符串和服务器端验证签名字符串的密钥。

>!API 密钥是构建腾讯云 API 请求的重要凭证，使用腾讯云 API 可以操作您名下的所有腾讯云资源，为了您的财产和服务安全，请妥善保存和定期更换密钥，当您更换密钥后，请及时删除旧密钥。
### MongoDB 用户名使用限制是什么？
腾讯云內建了 rwuser 和 mongouser 两个默认用户。內建用户的角色为 [readWriteAnyDatabase+dbAdmin](https://docs.mongodb.com/v3.0/reference/built-in-roles/)，即您可以用此用户读写任意数据库，但不具备高危操作的权限。
因 MongoDB 版本而异，部分实例只有 rwuser（对于这批实例腾讯云会进行升级，升级之前会联系您）。
您也可以使用腾讯云 MongoDB 控制台进行账号和权限管理以满足您的业务需要，详情参见 [限制说明](https://cloud.tencent.com/document/product/240/622)。
 
