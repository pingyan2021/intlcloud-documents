### 接口描述
本接口（ProcessEnding）用于结束进程，服务器进程状态更改为 TERMINATED，并回收进程相关资源。

### 参数描述

无参数。

### 返回值说明
- True：成功。
- False：失败。

包含错误消息的一般结果，具体类型为 [GenericOutcome](https://intl.cloud.tencent.com/document/product/1055/36700#jtlx)。

### 使用示例
```
 TencentCloud::Gse::GenericOutcome outcome = TencentCloud::Gse::Server::ProcessEnding();   
```
